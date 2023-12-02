<!-- /pages/blog/ssg/[id].vue -->

<template>
  <div>
    <a href="/blog/ssg">Back</a>
    <h3>{{ blog?.title || "" }}</h3>
    <p>{{ blog?.description || "" }}</p>
  </div>
</template>

<script setup>
import axios from 'axios';

// asyncData hanya dapat digunakan di halaman
export async function asyncData({ params }) {
  const { data } = await axios.get(`http://localhost:3100/api/blog/${params.id}`);
  return { blog: data.docs[0] };
}
</script>
