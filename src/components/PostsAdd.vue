<!-- <script setup>
import axios from 'axios';
import { reactive } from 'vue';


const form = reactive({
    title: '',
    description: ''
})
const handleSubmit = async () => {
    const newPost = {
        title: form.title,
        description: form.title
    }
    try {
        const response = await axios.post('http://localhost/belajar-api/insert-data.php/posts', newPost);
   console.log(response);
   
    } catch (error) {
        console.error("Error on posting data:", error);
    }
}

</script>

<template>
    <RouterLink :to="`/posts`" class="btn btn-green">Return to Posts</RouterLink>
    <div>
        <form @submit.prevent="handleSubmit">
            <label for="title">Title</label>
            <input 
            v-model="form.title" 
            type="text" 
            id="title" 
            name="title" 
            placeholder="Title">
            <label for="description">Description</label>
            <textarea 
            v-model="form.description" 
            id="description" 
            name="description">
            </textarea>
            <button type="submit" class="btn btn-green">Submit</button>
        </form>
    </div>
</template> -->

<!-- Terbaru -->

<!-- <script setup>
import axios from "axios";
import { reactive } from "vue";
import router from "@/router";

const form = reactive({
  student_no: "",
  student_name: "",
  student_class: "",
});
const handleSubmit = async () => {
  const newPost = {
    student_no: form.student_no,
    student_name: form.student_name,
    student_class: form.student_class,
  };
  try {
    const response = await axios.post(
      "http://localhost/belajar-api/insert-data.php",
      newPost
    );
    console.log(response);
    return router.push("/posts");
  } catch (error) {
    console.error("Error on posting data:", error);
  }
};
</script>

<template>
  <RouterLink :to="`/posts`" class="btn btn-green">Return to Posts</RouterLink>
  <div>
    <form @submit.prevent="handleSubmit">
      <label for="no">NO</label>
      <input
        v-model="form.student_no"
        type="text"
        id="no"
        name="no"
        placeholder="NO"
      />

      <label for="name">Name</label>
      <input
        v-model="form.student_name"
        type="text"
        id="name"
        name="name"
        placeholder="Name"
      />

      <label for="class">Class</label>
      <input
        v-model="form.student_class"
        id="class"
        name="class"
        placeholder="Class"
      />
      <button type="submit" class="btn btn-green">Submit</button>
    </form>
  </div>
</template> -->

<script setup>
import axios from "axios";
import { reactive } from "vue";
import router from "@/router";

const form = reactive({
  student_no: "",
  student_name: "",
  student_class: "",
});

const handleSubmit = async () => {
  const newPost = {
    student_no: form.student_no,
    student_name: form.student_name,
    student_class: form.student_class,
  };
  try {
    const response = await axios.post(
      "http://localhost/belajar-api/insert-data.php",
      newPost
    );
    console.log(response);
    return router.push("/posts");
  } catch (error) {
    console.error("Error on posting data:", error);
  }
};
</script>

<template>
  <div class="add-post-container">
    <div class="content">
      <h1 class="title">Add New Post</h1>
      <form @submit.prevent="handleSubmit" class="form">
        <div class="form-group">
          <label for="no">Student No</label>
          <input
            v-model="form.student_no"
            type="text"
            id="no"
            name="no"
            placeholder="Enter Student No"
            class="input"
          />
        </div>

        <div class="form-group">
          <label for="name">Student Name</label>
          <input
            v-model="form.student_name"
            type="text"
            id="name"
            name="name"
            placeholder="Enter Student Name"
            class="input"
          />
        </div>

        <div class="form-group">
          <label for="class">Student Class</label>
          <input
            v-model="form.student_class"
            id="class"
            name="class"
            placeholder="Enter Student Class"
            class="input"
          />
        </div>

        <button type="submit" class="btn btn-green">Submit</button>
      </form>
      <RouterLink :to="`/posts`" class="btn btn-gray">Return to Posts</RouterLink>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

.add-post-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  font-family: 'Inter', Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.add-post-container::before,
.add-post-container::after {
  content: '';
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
  z-index: 0;
}
.add-post-container::before {
  width: 400px;
  height: 400px;
  background: #43e97b;
  top: -120px;
  left: -120px;
  animation: float1 8s ease-in-out infinite alternate;
}
.add-post-container::after {
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
  margin-bottom: 1.5rem;
  color: #222;
  letter-spacing: 1px;
  position: relative;
  z-index: 1;
  text-shadow: 0 2px 12px rgba(60, 220, 132, 0.08);
}

.form {
  display: flex;
  flex-direction: column;
  gap: 1.3rem;
  margin-bottom: 1.5rem;
  position: relative;
  z-index: 1;
}

.form-group {
  text-align: left;
}

label {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  display: block;
  color: #222;
}

.input {
  width: 100%;
  padding: 0.75rem;
  border-radius: 0.75rem;
  border: none;
  font-size: 1rem;
  background: rgba(255,255,255,0.92);
  color: #222;
  box-shadow: 0 2px 8px rgba(60, 220, 132, 0.08);
  transition: box-shadow 0.2s, border 0.2s;
}

.input:focus {
  outline: none;
  box-shadow: 0 0 0 2px #43e97b;
}

.btn {
  padding: 0.9rem 1.5rem;
  border-radius: 0.75rem;
  font-size: 1.08rem;
  font-weight: 600;
  text-transform: uppercase;
  transition: all 0.25s cubic-bezier(.4,0,.2,1);
  display: inline-block;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: 0 2px 8px rgba(60, 220, 132, 0.12);
  margin-top: 0.5rem;
  background: linear-gradient(90deg, #43e97b 0%, #38f9d7 100%);
  color: #fff;
  border: none;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.btn-green {
  background: linear-gradient(90deg, #43e97b 0%, #38f9d7 100%);
  color: #fff;
}
.btn-green:hover, .btn-green:focus {
  filter: brightness(1.09);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 8px 32px rgba(60, 220, 132, 0.22);
  background: linear-gradient(90deg, #38f9d7 0%, #43e97b 100%);
}

.btn-gray {
  background: #757575;
  color: #fff;
}
.btn-gray:hover, .btn-gray:focus {
  background: #616161;
  filter: brightness(1.09);
  transform: translateY(-2px) scale(1.04);
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