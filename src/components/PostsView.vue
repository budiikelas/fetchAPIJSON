<!-- <script setup>
import axios from 'axios';
import { onMounted, reactive } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();

const postId = route.params.id;
const state = reactive({
    post: Object
})

onMounted(async () => {
    try {
        const response = await axios.get(`http://localhost:8080/posts/${postId}`);
        state.post = response.data;
    } catch (error) {
        console.log("Error while fetching: ", error);
    }
})


</script>
<template>
    <div class="center-container">
        <h1>{{ state.post.title }}</h1>
        <p>{{ state.post.description }}</p>
        <RouterLink :to="`/posts`" class="btn btn-green">Return to Posts</RouterLink>
    </div>
</template> -->

<!-- Terbaru -->

<!-- <script setup>
import axios from "axios";
import { onMounted, reactive } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();

const postId = route.params.id;
const state = reactive({
  post: Object,
});

onMounted(async () => {
  try {
    const response = await axios.get(
      `http://localhost/belajar-api/get-all-data.php/?id=${postId}`
    );
    state.post = response.data;
  } catch (error) {
    console.log("Error while fetching: ", error);
  }
});
</script>
<template>
  <div class="center-container">
    <h1>{{ state.post.student_no }}</h1>
    <p>{{ state.post.student_name }}</p>
    <p>{{ state.post.student_class }}</p>
    <RouterLink :to="`/posts`" class="btn btn-green"
      >Return to Posts</RouterLink
    >
  </div>
</template> -->

<script setup>
import axios from "axios";
import { onMounted, reactive } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();

const postId = route.params.id;
const state = reactive({
  post: Object,
});

onMounted(async () => {
  try {
    const response = await axios.get(
      `http://localhost/belajar-api/get-all-data.php/?id=${postId}`
    );
    state.post = response.data;
  } catch (error) {
    console.log("Error while fetching: ", error);
  }
});
</script>

<template>
  <div class="post-view-container">
    <div class="content">
      <h1 class="title">Post Details</h1>
      <div class="post-details">
        <p><strong>Student No:</strong> {{ state.post.student_no }}</p>
        <p><strong>Student Name:</strong> {{ state.post.student_name }}</p>
        <p><strong>Student Class:</strong> {{ state.post.student_class }}</p>
      </div>
      <RouterLink :to="`/posts`" class="btn btn-green">Return to Posts</RouterLink>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

.post-view-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  font-family: 'Inter', Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.post-view-container::before,
.post-view-container::after {
  content: '';
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
  z-index: 0;
}
.post-view-container::before {
  width: 400px;
  height: 400px;
  background: #43e97b;
  top: -120px;
  left: -120px;
  animation: float1 8s ease-in-out infinite alternate;
}
.post-view-container::after {
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

.post-details {
  text-align: left;
  margin-bottom: 2rem;
  font-size: 1.08rem;
  line-height: 1.7rem;
  color: #222;
}

.post-details p {
  margin: 0.5rem 0;
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
