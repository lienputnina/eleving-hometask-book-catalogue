<template>
  <input
    id="book-search"
    class="flex flex-grow border-slate-200 border-2 rounded h-8 text-slate-700 py-4 pl-9 bg-transparent"
    style="
      background-image: url(../assets/images/search.png);
      background-repeat: no-repeat;
      background-position-y: center;
    "
    name="book-search"
    type="search"
    v-model="userInput"
    placeholder="Search for a book"
  />
  <div class="mt-4 text-slate-500">
    <p>{{ resultsNumber }} results</p>
  </div>
  <div class="mt-2 mb-7 flex flex-col w-fit" v-if="!userInput">
    <h2 class="text-slate-950 mb-6 font-bold text-2xl">Explore books</h2>
    <img src="../assets/images/colouredBooks.png" alt="coloured-books" />
  </div>
  <!--FILTERED Books -->
  <div class="flex flex-row m-1.5 w-fit" v-for="book in filteredData">
    <img
      src="../assets/images/facebookScrabble.jpeg"
      class="w-20 h-28 rounded"
    />
    <div class="p-3">
      <NuxtLink
        :to="`/books/${book.id}`"
        class="font-bold hover:text-slate-600"
        >{{ book.title }}</NuxtLink
      >
      <p class="text-slate-600">{{ book.author }}</p>
      <p class="text-slate-600">{{ book.year }}</p>
      <p class="font-bold">{{ book.price }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import '../assets/css/main.css';

let resultsNumber = 1;
let filteredData;

const { data } = await useFetch<GetBooksResponse>(
  'http://localhost:5000/books/',
  {
    onResponse({ request, response, options }) {
      filteredData = response._data.filter((book) =>
        book.title.toLowerCase().includes('war'),
      );
    },
  },
);

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
