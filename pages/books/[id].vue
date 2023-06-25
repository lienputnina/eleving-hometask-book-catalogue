<template>
  <div class="flex">
    <img src="../../assets/images/backArrow.png" class="w-4 h-4 mt-1" />
    <NuxtLink :to="`/`" class="hover:underline">Explore</NuxtLink>
  </div>
  <BookDetails :book="book" :id="id" />
  <Reviews :book="book" />
  <AddReview :book="book" :id="id" />
</template>

<script setup>
import AddReview from '../../components/AddReview.vue';
import BookDetails from '../../components/BookDetails.vue';
import Reviews from '../../components/Reviews.vue';

const { id } = useRoute().params;
const uri = 'http://localhost:5000/books/' + id;

const { data: book } = await useFetch(uri);
</script>
