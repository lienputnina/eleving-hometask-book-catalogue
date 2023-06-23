<template>
  <div class="flex flex-row m-1.5">
    <img
      src="../../assets/images/facebookScrabble.jpeg"
      class="w-20 h-28 rounded mt-1"
    />
    <div class="px-3 py-2">
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
  <p class="text-slate-700 text-left ml-2">{{ book.description }}</p>
</template>

<script setup>
const { id } = useRoute().params;
const uri = 'http://localhost:5000/books/' + id;

const { data: book } = await useFetch(uri);
</script>
