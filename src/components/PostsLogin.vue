<template>
  <IonPage class="login-page">
    <IonContent class="ion-padding">
      <div class="login-container">
        <div class="content">
          <h1 class="title">Login</h1>
          <form @submit.prevent="handleLogin" class="form">
            <div class="form-group">
              <span class="input-icon">👤</span>
              <IonInput
                label="Username"
                labelPlacement="floating"
                fill="outline"
                v-model="username"
                class="input"
                required
              />
            </div>
            <div class="form-group">
              <span class="input-icon">🔒</span>
              <IonInput
                label="Password"
                labelPlacement="floating"
                fill="outline"
                type="password"
                v-model="password"
                class="input"
                required
              />
            </div>
            <IonButton expand="block" class="btn btn-green" type="submit">
              Login
            </IonButton>
          </form>
        </div>
      </div>
      <IonAlert
        :is-open="showAlert"
        :header="alertHeader"
        :message="alertMessage"
        :buttons="alertButtons"
        @didDismiss="showAlert = false"
      />
    </IonContent>
  </IonPage>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'
import { useRouter } from 'vue-router'
import {
  IonPage,
  IonContent,
  IonInput,
  IonButton,
  IonAlert
} from '@ionic/vue'

const username = ref('')
const password = ref('')
const router = useRouter()

// Alert control
const showAlert = ref(false)
const alertHeader = ref('')
const alertMessage = ref('')
const alertButtons = ref(['OK'])

const handleLogin = async () => {
  if (!username.value || !password.value) {
    alertHeader.value = 'Validasi'
    alertMessage.value = 'Username dan password wajib diisi.'
    alertButtons.value = ['OK']
    showAlert.value = true
    return
  }

  try {
    const response = await axios.post('http://localhost/belajar-api/login.php', {
      username: username.value,
      password: password.value
    })

    if (response.data.status === 'success') {
      localStorage.setItem('user', JSON.stringify(response.data.data))
      alertHeader.value = 'Login Berhasil'
      alertMessage.value = 'Selamat datang!'
      alertButtons.value = [{
        text: 'OK',
        handler: () => {
          router.push('/home')
        }
      }]
      showAlert.value = true
    } else {
      alertHeader.value = 'Login Gagal'
      alertMessage.value = 'Username atau password salah.'
      alertButtons.value = ['OK']
      showAlert.value = true
    }
  } catch (error) {
    alertHeader.value = 'Error'
    alertMessage.value = 'Tidak dapat terhubung ke server.'
    alertButtons.value = ['OK']
    showAlert.value = true
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

.login-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  font-family: 'Inter', Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.login-page::before,
.login-page::after {
  content: '';
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
  z-index: 0;
}
.login-page::before {
  width: 400px;
  height: 400px;
  background: #43e97b;
  top: -120px;
  left: -120px;
  animation: float1 8s ease-in-out infinite alternate;
}
.login-page::after {
  width: 300px;
  height: 300px;
  background: #38f9d7;
  bottom: -100px;
  right: -100px;
  animation: float2 10s ease-in-out infinite alternate;
}

@keyframes float1 {
  0% { transform: translateY(0) scale(1);}
  100% { transform: translateY(40px) scale(1.1);}
}
@keyframes float2 {
  0% { transform: translateY(0) scale(1);}
  100% { transform: translateY(-30px) scale(1.05);}
}

.login-container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1;
  width: 100vw;
}

.content {
  width: 100%;
  max-width: 400px;
  background: rgba(255,255,255,0.18);
  border-radius: 2rem;
  padding: 2.5rem 2rem 2rem 2rem;
  box-shadow: 0 8px 32px 0 rgba(31,38,135,0.18);
  backdrop-filter: blur(16px);
  border: 1.5px solid rgba(255,255,255,0.25);
  color: #222;
  text-align: center;
  transition: box-shadow 0.3s, border 0.3s;
  position: relative;
  overflow: hidden;
}

.content::before {
  content: '';
  position: absolute;
  top: -40px;
  right: -40px;
  width: 120px;
  height: 120px;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  opacity: 0.18;
  border-radius: 50%;
  z-index: 0;
}

.title {
  font-size: 2.3rem;
  font-weight: 700;
  margin-bottom: 2.2rem;
  color: #222;
  letter-spacing: 1px;
  position: relative;
  z-index: 1;
  text-shadow: 0 2px 12px rgba(60, 220, 132, 0.08);
}

.form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  position: relative;
  z-index: 1;
}

.form-group {
  text-align: left;
  position: relative;
}

.input {
  --background: rgba(255,255,255,0.92);
  --color: #222;
  border-radius: 1rem;
  font-size: 1.12rem;
  box-shadow: 0 2px 12px rgba(60, 220, 132, 0.10);
  transition: box-shadow 0.2s, border 0.2s;
  padding-left: 2.5rem;
  min-height: 48px;
}

.input:focus-within {
  box-shadow: 0 4px 24px rgba(60, 220, 132, 0.18);
  border: 1.5px solid #43e97b;
}

.form-group .input-icon {
  position: absolute;
  left: 0.8rem;
  top: 50%;
  transform: translateY(-50%);
  font-size: 1.3rem;
  color: #43e97b;
  opacity: 0.8;
  z-index: 2;
  pointer-events: none;
}

.btn {
  padding: 1rem 1.5rem;
  border-radius: 1rem;
  font-size: 1.12rem;
  font-weight: 700;
  text-transform: uppercase;
  transition: all 0.25s cubic-bezier(.4,0,.2,1);
  display: inline-block;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: 0 2px 12px rgba(60, 220, 132, 0.14);
  margin-top: 0.5rem;
  background: linear-gradient(90deg, #43e97b 0%, #38f9d7 100%);
  color: #fff;
  border: none;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.btn-green:hover, .btn-green:focus {
  filter: brightness(1.09);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 8px 32px rgba(60, 220, 132, 0.22);
  background: linear-gradient(90deg, #38f9d7 0%, #43e97b 100%);
}

.btn-green::after {
  content: '';
  position: absolute;
  left: 50%;
  top: 50%;
  width: 0;
  height: 0;
  background: rgba(255,255,255,0.18);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.4s, height 0.4s;
  z-index: 0;
}

.btn-green:active::after {
  width: 200%;
  height: 200%;
}

@media (max-width: 500px) {
  .content {
    padding: 1.5rem 0.5rem 1rem 0.5rem;
    max-width: 95vw;
  }
  .title {
    font-size: 1.5rem;
  }
}

/* Animasi masuk */
.content {
  animation: fadeInUp 0.8s cubic-bezier(.4,0,.2,1);
}
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(40px) scale(0.98);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
</style>