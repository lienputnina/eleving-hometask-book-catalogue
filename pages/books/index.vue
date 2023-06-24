<template>
  <div>
    <div v-for="book in books" :key="`${book.id}`">
      <NuxtLink :to="`/books/${book.id}`">{{ book.title }}</NuxtLink>
    </div>
  </div>
</template>

<script setup>
const { data: books } = await useFetch('http://localhost:5000/books/');
</script>

<style scoped></style>
