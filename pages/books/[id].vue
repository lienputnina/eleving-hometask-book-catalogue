<template>
  <div class="flex">
    <img src="../../assets/images/backArrow.png" class="w-4 h-4 mt-1" />
    <NuxtLink :to="`/`" class="hover:underline">Explore</NuxtLink>
  </div>
  <div class="flex flex-row m-1.5">
    <img
      :src="book.image"
      class="w-28 h-28 rounded mt-1"
      al="book cover image"
    />
    <div class="px-3 py-2 text-sm">
      <p class="font-bold">{{ book.title }}</p>
      <p class="text-slate-600">{{ book.author }}</p>
      <p class="font-bold">{{ book.price }}</p>
      <p class="text-slate-600">{{ book.year }}</p>
      <p class="text-slate-600">{{ book.publisher }}</p>
    </div>
  </div>
  <div class="flex flex-row mt-5 mb-5 ml-2 self-center">
    <p class="text-slate-700 mr-2">{{ book.rating }}</p>
    <img src="../../assets/images/rating.png" class="w-24 h-5" />
  </div>
  <p class="text-slate-700 text-left ml-2 text-sm">{{ book.description }}</p>
  <Review :book="book" :id="id" />
</template>

<script setup>
import Review from '../../components/Review.vue';

const { id } = useRoute().params;
const uri = 'http://localhost:5000/books/' + id;

const { data: book } = await useFetch(uri);
</script>
