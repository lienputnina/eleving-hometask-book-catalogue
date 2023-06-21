<template>
  <HeaderComponent />
  <div class="book-details-main">
    <div>Book details for {{ id }}</div>
    <div class="book-details">
      <p>{{ book.image }}</p>
      <p>{{ book.title }}</p>
      <p>{{ book.author }}</p>
      <p>{{ book.price }}</p>
      <p>{{ book.year }}</p>
      <p>{{ book.publisher }}</p>
    </div>
  </div>
</template>

<script setup>
import HeaderComponent from "~/components/HeaderComponent.vue";

const { id } = useRoute().params;
const uri = "http://localhost:5000/books/" + id;

const { data: book } = await useFetch(uri);
</script>

<style scoped>
.book-details-main {
  margin: 15px;
}
.book-details {
  border: 2px solid black;
  width: fit-content;
  padding: 10px;
  margin-top: 10px;
}
</style>
