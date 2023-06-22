<template>
  <input
    id="book-search"
    class="search-input"
    name="book-search"
    type="search"
    v-model="userInput"
  />
  <!--FILTER Books-->
  <div class="test" v-for="book in filteredData">
    <p>{{ book.title }}</p>
  </div>
  <div>
    <h2>Explore books</h2>
    <img src="../assets/ColouredBooks.png" alt="coloured-books" />
  </div>
</template>

<script setup lang="ts">
let filteredData;

const { data } = await useFetch<GetBooksResponse>(
  'http://localhost:5000/books/',
  {
    onResponse({ request, response, options }) {
      filteredData = response._data.filter((book) =>
        book.title.toLowerCase().includes('war'),
      );

      if (userInput?.value) {
        filteredData = response._data.filter((book) =>
          book.title.toLowerCase().includes(userInput.value),
        );
      }
    },
  },
);

import { ref } from 'vue';
let userInput = ref('');

interface Book {
  id: number;
  title: string;
  author: string;
  description: string;
  image: string;
  rating: number;
  publisher: string;
  isbn: string;
  price: string;
  year: string;
}

interface GetBooksResponse {
  books: Book[];
}
</script>

<style>
.test-books {
  border: 2px solid black;
  width: fit-content;
}
div {
  margin: 10px;
  font-family: Arial, Helvetica, sans-serif;
}
form {
  margin-top: 20px;
}
input {
  margin-left: 5px;
  margin-right: 5px;
}
.search-input {
  height: 30px;
  width: fit-content;
}

.book-class {
  display: flex;
}
</style>
