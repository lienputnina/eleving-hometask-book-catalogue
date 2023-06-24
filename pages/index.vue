<template>
  <input
    id="book-search"
    class="flex flex-grow border-slate-200 border-2 rounded h-8 text-slate-700 py-4 pl-9 bg-transparent w-full max-w-lg"
    style="
      background-image: url(../assets/images/search.png);
      background-repeat: no-repeat;
      background-position-y: center;
    "
    name="book-search"
    type="search"
    v-model="userSearchInput"
    placeholder="Search for a book"
  />
  <div class="mt-4 text-slate-500 text-sm ml-1" v-if="userSearchInput">
    <p>{{ resultsNumber }} results</p>
  </div>
  <div class="mt-6 mb-7 flex flex-col w-full" v-if="!userSearchInput">
    <h2 class="text-slate-950 mb-6 font-bold text-2xl">Explore books</h2>
    <img
      src="../assets/images/colouredBooks.png"
      alt="coloured-books"
      class="w-32 h-32 max-h-sm max-w-sm"
    />
  </div>
  <ul v-for="book in filteredBooks">
    <li class="flex flex-row m-1.5 w-fit">
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
    </li>
  </ul>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import '../assets/css/main.css';

let resultsNumber = 1;

let filteredBooks;

const { data } = await useFetch<GetBooksResponse>(
  'http://localhost:5000/books/',
  {
    onResponse({ request, response, options }) {
      filteredBooks = response._data.filter((book: Book) =>
        book.title.toLowerCase().includes('war'),
      );
    },
  },
);
let userSearchInput = ref('');

export interface Book {
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
  review: string[];
}

export interface GetBooksResponse {
  books: Book[];
}
</script>
