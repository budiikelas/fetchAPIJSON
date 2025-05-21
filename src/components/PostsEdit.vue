<!-- <script setup>
import axios from 'axios';
import { onMounted, reactive } from 'vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();

const postId = route.params.id;

const form = reactive({
    title: '',
    description: ''
})

onMounted( async () => {
    try {
        const response = await axios.get(`http://localhost/belajar-api/update-data.php/posts/${postId}`);
        form.title = response.data.title;
        form.description = response.data.description;
    } catch (error) {
        console.log("Error fetching post", response);
    }
})

const handleSubmit = async () => {
    const updatePost = {
        title: form.title,
        description: form.description
    }

    try {
        const response = await axios.put(`http://localhost:8080/posts/${postId}`, updatePost);
        router.push(`/posts/${response.data.id}`);
    } catch (error) {
        console.error("Error updating post", error);
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
</template>

<style scoped>
.form-container {
    max-width: 400px;
    margin: 0 auto;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-bottom: 5px;
    font-weight: bold;
}

input, textarea, button {
    margin-bottom: 15px;
    padding: 10px;
    font-size: 1rem;
}

textarea {
    resize: vertical;
}

button {
    background-color: #da7cb5; 
    color: white; 
    border: none; 
    border-radius: 5px; 
    cursor: pointer; 
    transition: background-color 0.3s ease; 
}

button:hover {
    background-color: #da7cb5; 
}
</style> -->

<!-- Terbaru -->

<!-- <script setup>
import axios from "axios";
import { onMounted, reactive } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();

const postId = route.params.id;

const form = reactive({
  student_no: "",
  student_name: "",
  student_class: "",
});

onMounted(async () => {
  try {
    const response = await axios.get(
      `http://localhost/belajar-api/get-all-data.php/?id=${postId}`
    );
    form.student_no = response.data.student_no;
    form.student_name = response.data.student_name;
    form.student_class = response.data.student_class;
  } catch (error) {
    console.log("Error fetching post", response);
  }
});

const handleSubmit = async () => {
  const updatePost = {
    student_id: postId,
    student_no: form.student_no,
    student_name: form.student_name,
    student_class: form.student_class,
  };

  try {
    const response = await axios.put(
      "http://localhost/belajar-api/update-data.php",
      updatePost
    );
    console.log(response);

    router.push(`/posts/${postId}}`);
  } catch (error) {
    console.error("Error updating post", error);
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
import { onMounted, reactive } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();

const postId = route.params.id;

const form = reactive({
  student_no: "",
  student_name: "",
  student_class: "",
});

onMounted(async () => {
  try {
    const response = await axios.get(
      `http://localhost/belajar-api/get-all-data.php/?id=${postId}`
    );
    form.student_no = response.data.student_no;
    form.student_name = response.data.student_name;
    form.student_class = response.data.student_class;
  } catch (error) {
    console.log("Error fetching post", error);
  }
});

const handleSubmit = async () => {
  const updatePost = {
    student_id: postId,
    student_no: form.student_no,
    student_name: form.student_name,
    student_class: form.student_class,
  };

  try {
    const response = await axios.put(
      "http://localhost/belajar-api/update-data.php",
      updatePost
    );
    console.log(response);

    router.push(`/posts/${postId}`);
  } catch (error) {
    console.error("Error updating post", error);
  }
};
</script>

<template>
  <div class="edit-post-container">
    <div class="content">
      <h1 class="title">Edit Post</h1>
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

.edit-post-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  font-family: 'Inter', Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.edit-post-container::before,
.edit-post-container::after {
  content: '';
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
  z-index: 0;
}
.edit-post-container::before {
  width: 400px;
  height: 400px;
  background: #43e97b;
  top: -120px;
  left: -120px;
  animation: float1 8s ease-in-out infinite alternate;
}
.edit-post-container::after {
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