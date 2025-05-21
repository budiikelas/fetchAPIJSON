<!-- <script setup>
import { RouterLink } from 'vue-router';
</script>
<template>
    <div class="center-container">
        <h1>Welcome to Vue Post CRUD tutorial.</h1>
        <RouterLink :to="`/posts`" class="btn btn-green">Go To Posts</RouterLink>
    </div>
</template> -->

<script setup>
import { RouterLink, useRouter } from 'vue-router';

const router = useRouter();

function handleLogout() {
  localStorage.removeItem('user');
  router.push('/'); // pastikan route '/login' mengarah ke PostsLogin.vue
}
</script>

<template>
  <div class="home-container">
    <div class="content">
      <h1 class="title">Welcome to Vue Post CRUD Tutorial</h1>
      <p class="subtitle">Manage your posts efficiently and easily.</p>
      <div class="actions">
        <RouterLink :to="`/posts`" class="btn btn-green">Go To Posts</RouterLink>
        <button class="btn btn-red" @click="handleLogout">Logout</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

.home-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  font-family: 'Inter', Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.home-container::before,
.home-container::after {
  content: '';
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
  z-index: 0;
}
.home-container::before {
  width: 400px;
  height: 400px;
  background: #43e97b;
  top: -120px;
  left: -120px;
  animation: float1 8s ease-in-out infinite alternate;
}
.home-container::after {
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
  animation: fadeInUp 0.8s cubic-bezier(.4,0,.2,1);
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
  margin-bottom: 1.2rem;
  color: #222;
  letter-spacing: 1px;
  position: relative;
  z-index: 1;
  text-shadow: 0 2px 12px rgba(60, 220, 132, 0.08);
}

.subtitle {
  font-size: 1.15rem;
  margin-bottom: 2.2rem;
  color: #333;
  z-index: 1;
  position: relative;
}

.actions {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-top: 1.5rem;
  z-index: 1;
  position: relative;
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

.btn-red {
  background: linear-gradient(90deg, #ff5858 0%, #f09819 100%);
  color: #fff;
}

.btn-red:hover, .btn-red:focus {
  filter: brightness(1.09);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 8px 32px rgba(255, 88, 88, 0.18);
  background: linear-gradient(90deg, #f09819 0%, #ff5858 100%);
}

.btn-green::after, .btn-red::after {
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

.btn-green:active::after, .btn-red:active::after {
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