<template>
  <SearchComponent />
  <h2>Explore books</h2>
  <div>
    <img src="../assets/ColouredBooks.png" alt="colored-books" />
  </div>
  <NuxtLink to="/singleBook"> Single Book Page </NuxtLink>
</template>

<script lang="ts">
// import SearchComponent from "~/.nuxt/components/SearchComponent.vue";

// export default {
//   name: "Index",
//   components: {
//     SearchComponent,
//   },
// };
</script>

<style>
div {
  margin: 10px;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
