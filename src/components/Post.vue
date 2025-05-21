<!-- <script setup>
import axios from "axios";
import { defineProps } from "vue";
import { RouterLink, useRouter } from "vue-router";

const router = useRouter();

const props = defineProps({
  post: Object,
});

const deletePost = async (postId) => {
  try {
    const confirm = window.confirm(
      "Are you sure you want to delete this posts?"
    );
    if (confirm) {
      await axios.delete(
        `http://localhost/belajar-api/delete-data.php/posts/${postId}`
      );
      router.push("/");
    }
  } catch (error) {
    console.error("Error deleting post: ", error);
  }
};
</script>
<template>
  <tr>
    <td>{{ post.student_id }}</td>
    <td>{{ post.student_name }}</td>
    <td>
      <RouterLink :to="`/posts/${post.student_id}`" class="btn btn-green">O</RouterLink>
      <RouterLink :to="`/posts/edit/${post.student_id}`" class="btn btn-blue"
        >/</RouterLink
      >
      <button @click="deletePost(post.student_id)" class="btn btn-red">X</button>
    </td>
  </tr>
</template> -->

<!-- Terbaru -->

<script setup>
import axios from "axios";
import { defineProps } from "vue";
import { RouterLink, useRouter } from "vue-router";

const router = useRouter();

const props = defineProps({
  post: Object,
});

const deletePost = async (deletedId) => {
  try {
    const confirm = window.confirm(
      "Are you sure you want to delete this posts?"
    );
    if (confirm) {
      const res = await axios.delete(
        `http://localhost/belajar-api/delete-data.php?student_id=${deletedId}`
      );
      console.log("Delete success:", res.data);
      router.push("/");
    }
  } catch (error) {
    console.error(
      "Error deleting post: ",
      error.response?.data || error.message
    );
  }
};
</script>
<template>
  <tr>
    <td>{{ post.student_no }}</td>
    <td>{{ post.student_name }}</td>
    <td>{{ post.student_class }}</td>
    <td>
      <RouterLink :to="`/posts/${post.student_id}`" class="btn btn-green"
        >View</RouterLink
      >
      <RouterLink :to="`/posts/edit/${post.student_id}`" class="btn btn-blue"
        >Update</RouterLink
      >
      <button @click="deletePost(post.student_id)" class="btn btn-red">
        Delete
      </button>
    </td>
  </tr>
</template>
