<template>
  <div class="flex flex-col self-center">
    <div>
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
    </div>
    <div class="mt-4 text-slate-500">
      <p>{{ resultsNumber }} results</p>
    </div>
    <div class="mt-2 flex flex-col w-fit">
      <h2 class="text-slate-950 mb-6 font-bold text-2xl">Explore books</h2>
      <img src="../assets/images/ColouredBooks.png" alt="coloured-books" />
    </div>
    <!--FILTERED Books -->
    <ul class="flex flex-row m-1.5 w-fit" v-for="book in filteredData">
      <img
        src="../assets/images/FacebookScrabble.jpeg"
        class="w-20 h-28 rounded"
      />
      <!-- <img src="{{ book.image }}" /> -->
      <div class="p-3">
        <li class="font-bold">{{ book.title }}</li>
        <li class="text-slate-700">{{ book.author }}</li>
        <li class="text-slate-600">{{ book.year }}</li>
        <li class="font-bold">{{ book.price }}</li>
      </div>
    </ul>
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
