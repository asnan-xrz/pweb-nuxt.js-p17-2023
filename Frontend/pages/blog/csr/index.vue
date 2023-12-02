<!-- /pages/blog/csr/index.vue -->

<template>
  <div>
    <a href="/blog">Back</a>
    <h1>Product with CSR</h1>
    <div style="margin-top: 20px">
      <!-- <div v-if="blogs == null">Fetching data on client ...</div> -->
      <div v-for="(blog, idx) in blogs" :key="idx">
        <h5>{{ blog.title }}</h5>
        <p>{{ blog.description }}</p>
        <a :href="'/blog/csr/' + blog.id" style="color: black;">
          <p>Open csr</p>
        </a>
        <hr />
      </div>
    </div>
  </div>
</template>


<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const blogs = ref(null);

onMounted(async () => {
  const { data } = await axios.get("http://localhost:3100/api/blog");
  blogs.value = data.docs;
});
</script>