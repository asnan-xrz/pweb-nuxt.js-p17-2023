<!-- /pages/blog/ssg/index.vue -->

<template>
  <div>
    <a href="/blog">Back</a>
    <h1>Blog with SSG</h1>

    <div style="margin-top: 20px" v-if="blogs">
      <div v-for="(blog, idx) in blogs" :key="idx">
        <h5>{{ blog.title }}</h5>
        <nuxt-link :to="'/blog/ssg/' + blog.id">
          <p>Open ssg</p>
        </nuxt-link>
        <hr />
      </div>
    </div>
    <p v-else>Loading...</p>
  </div>
</template>

<script setup>
import axios from 'axios';

// asyncData hanya dapat digunakan di halaman
export async function asyncData() {
  const { data } = await axios.get("http://localhost:3100/api/blog");
  return { blogs: data.docs };
}
</script>
