<!-- /pages/blog/csr/[id].vue -->

<template>
    <div>
      <a href="/blog/csr">Back</a>
      <p v-if="blog == null">Fetching data on client ...</p>
      <h3>{{ blog?.title || "" }}</h3>
      <p>{{ blog?.description || "" }}</p>
      <p>{{ blog?.keywords || "" }}</p>
    </div>
  </template>
  
  <script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const blog = ref(null);
const route = useRoute()

onMounted(async () => {
    console.log(route)
  const { data } = await axios.get("http://localhost:3100/api/blog/" + route.params.id);
  blog.value = data.docs[0]; // Assuming you want to access the first blog post
});
</script>
  