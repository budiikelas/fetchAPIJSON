<!-- <script setup>
import { onMounted, reactive } from 'vue';
import { RouterLink } from 'vue-router';
import axios from 'axios';
import Post from '@/components/Post.vue';

const state = reactive({
    posts: []
})

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost/belajar-api/get-all-data.php');
    state.posts = response.data;
  } catch (error) {
    console.error('Error fetching jobs:', error);
  }
});
</script>
<template>
  <div class="center-container">
    <h1>All Post</h1> 
    <RouterLink :to="`/`" class="btn btn-blue">Go to Home</RouterLink>
    <RouterLink :to="`/posts/add`" class="btn btn-green">Add Post</RouterLink>
    <br />
    <br />
    <table id="posts">
        <tr>
            <th>No</th>
            <th>Nama</th>
            <th>Kelas</th>
            <th>Action</th>
        </tr>
        <Post v-for="post in state.posts" :key="post.student_id" :post="post"/>
    </table>
  </div>
</template> -->

<!-- Terbaru -->

<!-- <script setup>
import { onMounted, reactive } from "vue";
import { RouterLink } from "vue-router";
import axios from "axios";
import Post from "@/components/Post.vue";

const state = reactive({
  posts: [],
});

onMounted(async () => {
  try {
    const response = await axios.get(
      "http://localhost/belajar-api/get-all-data.php"
    );
    state.posts = response.data;
  } catch (error) {
    console.error("Error fetching jobs:", error);
  }
});
</script>
<template>
  <div class="center-container">
    <h1>All Post</h1>
    <RouterLink :to="`/`" class="btn btn-blue">Go to Home</RouterLink>
    <RouterLink :to="`/posts/add`" class="btn btn-green">Add Post</RouterLink>
    <br />
    <br />
    <table id="posts" border="1">
      <tr>
        <th>No</th>
        <th>Name</th>
        <th>Class</th>
        <th>Action</th>
      </tr>
      <Post v-for="post in state.posts" :key="post.id" :post="post" />
    </table>
  </div>
</template>

<style scoped>
.center-container {
  padding: 20px;
  color: white;
}
table {
  width: 100%;
  border-collapse: collapse;
}
th,
td,
tr {
  padding: 8px;
  text-align: left;
  color: white;
  align-items: center;
  text-align: center;
}
</style> -->

<script setup>
import { onMounted, reactive } from "vue";
import { RouterLink } from "vue-router";
import axios from "axios";
import Post from "@/components/Post.vue";

const state = reactive({
  posts: [],
});

onMounted(async () => {
  try {
    const response = await axios.get(
      "http://localhost/belajar-api/get-all-data.php"
    );
    state.posts = response.data;
  } catch (error) {
    console.error("Error fetching posts:", error);
  }
});
</script>

<template>
  <div class="posts-container">
    <div class="content">
      <h1 class="title">All Posts</h1>
      <div class="actions">
        <RouterLink :to="`/home`" class="btn btn-blue">Go to Home</RouterLink>
        <RouterLink :to="`/posts/add`" class="btn btn-green"
          >Add Post</RouterLink
        >
      </div>
      <table class="posts-table">
        <thead>
          <tr>
            <th>No</th>
            <th>Name</th>
            <th>Class</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <Post
            v-for="post in state.posts"
            :key="post.student_id"
            :post="post"
          />
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

.posts-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  font-family: 'Inter', Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.posts-container::before,
.posts-container::after {
  content: '';
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
  z-index: 0;
}
.posts-container::before {
  width: 400px;
  height: 400px;
  background: #43e97b;
  top: -120px;
  left: -120px;
  animation: float1 8s ease-in-out infinite alternate;
}
.posts-container::after {
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
  max-width: 900px;
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

.actions {
  display: flex;
  justify-content: flex-end;
  gap: 1rem;
  margin-bottom: 1.5rem;
  z-index: 1;
  position: relative;
}

.btn {
  padding: 0.7rem 1.3rem;
  border-radius: 1rem;
  font-size: 1.08rem;
  font-weight: 700;
  text-transform: uppercase;
  transition: all 0.25s cubic-bezier(.4,0,.2,1);
  display: inline-block;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: 0 2px 12px rgba(60, 220, 132, 0.14);
  border: none;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.btn-action {
  padding: 0.3rem 0.9rem;
  font-size: 0.95rem;
  border-radius: 0.6rem;
  min-width: 60px;
  min-height: 32px;
  line-height: 1.1;
  margin: 0;
  box-shadow: none;
}

.btn-blue {
  background: linear-gradient(90deg, #1976d2 0%, #43e97b 100%);
  color: #fff;
}
.btn-blue:hover, .btn-blue:focus {
  filter: brightness(1.09);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 8px 32px rgba(25, 118, 210, 0.18);
  background: linear-gradient(90deg, #43e97b 0%, #1976d2 100%);
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

.btn-yellow {
  background: linear-gradient(90deg, #f9d423 0%, #ff4e50 100%);
  color: #fff;
}
.btn-yellow:hover, .btn-yellow:focus {
  filter: brightness(1.09);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 8px 32px rgba(249, 212, 35, 0.18);
  background: linear-gradient(90deg, #ff4e50 0%, #f9d423 100%);
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

.btn-blue::after, .btn-green::after, .btn-yellow::after, .btn-red::after {
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
.btn-blue:active::after, .btn-green:active::after, .btn-yellow:active::after, .btn-red:active::after {
  width: 200%;
  height: 200%;
}

.action-buttons {
  display: flex;
  gap: 0.3rem;
  justify-content: center;
}

.posts-table {
  width: 100%;
  border-collapse: collapse;
  background: rgba(255,255,255,0.12);
  border-radius: 1rem;
  overflow: hidden;
  margin-top: 1rem;
  box-shadow: 0 2px 12px rgba(60, 220, 132, 0.10);
}

.posts-table th,
.posts-table td {
  padding: 1rem;
  text-align: center;
  color: #222;
  border-bottom: 1px solid rgba(67, 233, 123, 0.12);
  background: rgba(255,255,255,0.10);
}

.posts-table th {
  background: rgba(67, 233, 123, 0.10);
  font-weight: bold;
  color: #222;
}

.posts-table tr:last-child td {
  border-bottom: none;
}

.posts-table tr:hover {
  background: rgba(67, 233, 123, 0.08);
  transition: background 0.2s;
}

@media (max-width: 900px) {
  .content {
    max-width: 98vw;
    padding: 1.2rem 0.2rem 1rem 0.2rem;
  }
  .posts-table th, .posts-table td {
    padding: 0.5rem;
    font-size: 0.98rem;
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
