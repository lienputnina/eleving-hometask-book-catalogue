<template>
  <form @submit="onSubmit">
    <label for="book-search">Search Books:</label>
    <input type="search" id="book-search" name="book-search" />
    <input type="submit" />
  </form>
</template>

<script lang="ts">
export default {
  name: "SearchComponent",
  methods: {
    onSubmit() {
      // event.preventDefault();
      console.log("Search submitted");
    },
  },
};
</script>

<style scoped>
form {
  margin-top: 20px;
}
input {
  margin-left: 5px;
  margin-right: 5px;
}
</style>
