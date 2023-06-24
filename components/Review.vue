<template>
  <div class="mt-7 mx-1.5">
    <div>
      <h1 class="text-xl font-bold mb-5">Write a review</h1>
    </div>
    <form class="flex flex-col w-full max-w-sm mt-4">
      <label id="review-label" class="font-bold mb-5">
        Rate the book
        <img
          src="../../assets/images/rating.png"
          alt="book rating stars"
          class="w-24 h-5 mt-2"
        />
      </label>
      <input
        id="review-input"
        type="text"
        class="border-slate-200 border-2 rounded p-1.5 w-full"
        v-model="userInput"
        aria-labelledby="review-label"
      />
      <button
        class="border-cyan-700 border-2 rounded-2xl w-full p-1.5 mt-4 text-sm text-cyan-700 font-bold"
        type="button"
        @click="onSubmit()"
        v-if="!isReviewSubmitted"
      >
        Submit review
      </button>
      <p
        v-if="isReviewSubmitted"
        class="bg-sky-200 rounded-md py-1 px-1.5 font-bold mt-8 w-fit"
      >
        Thank you! Review received.
      </p>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const { book, id } = defineProps(['book', 'id']);

let bookWithReview = book;

let userInput = ref('');

let isReviewSubmitted: boolean = false;

const onSubmit = async () => {
  if (!userInput.value) {
    alert('Please add a review');
  } else {
    const newBook = {
      ...bookWithReview,
      review: [...(bookWithReview.review || []), userInput.value],
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

  userInput.value = '';
};
</script>
