<template>
  <div class="mt-6 mx-1.5">
    <form class="flex flex-col w-full max-w-sm mt-4" v-if="!isReviewSubmitted">
      <h2 class="text-xl font-bold mb-4">Write a review</h2>
      <label id="review-label" class="font-bold mb-5">
        Rate the book
        <img
          src="../assets/images/rating.png"
          alt="book rating stars"
          class="w-24 h-5 mt-2"
        />
      </label>
      <input
        id="review-input"
        type="text"
        class="border-slate-200 border-2 rounded p-1.5 w-full shadow-md shadow-slate-100 hover:shadow-lg hover:shadow-slate-200"
        v-model="reviewText"
        aria-labelledby="review-label"
      />
      <button
        class="border-cyan-700 border-2 rounded-2xl w-full p-1.5 mt-4 text-sm text-cyan-700 font-bold hover:text-cyan-600 hover:border-cyan-600 shadow-slate-100 hover:shadow-lg hover:shadow-slate-200"
        type="button"
        @click="onSubmit()"
      >
        Submit review
      </button>
    </form>
    <p
      class="bg-sky-200 rounded-md py-1 px-1.5 font-bold mt-8 w-fit"
      v-if="isReviewSubmitted"
    >
      Thank you! Review received.
    </p>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const { book, id } = defineProps(['book', 'id']);

let bookWithReview = book;
let reviewText = ref('');
let isReviewSubmitted: boolean = false;

const onSubmit = async () => {
  if (!reviewText.value) {
    alert('Please add a review');
  } else {
    const newBook = {
      ...bookWithReview,
      reviews: [...(bookWithReview.reviews || []), reviewText.value],
    };

    await $fetch(`http://localhost:5000/books/${id}`, {
      method: 'PUT',
      headers: {
        Accept: ' application/json',
      },
      body: JSON.stringify(newBook),
    });

    const { data } = await useFetch(`http://localhost:5000/books/${id}`);
    bookWithReview = data.value;
  }

  isReviewSubmitted = true;

  reviewText.value = '';
};
</script>
