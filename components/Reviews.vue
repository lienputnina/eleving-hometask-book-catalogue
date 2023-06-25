<template>
  <div class="mx-1.5 mt-1.5">
    <h1 class="font-bold mb-1">Customer reviews</h1>
    <ul v-for="review in book.reviews">
      <li>"{{ review }}"</li>
    </ul>
  </div>
</template>

<script lang="ts" setup>
const { book } = defineProps(['book']);
</script>
