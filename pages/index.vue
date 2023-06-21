<template>
  <HeaderComponent />
  <SearchComponent />
  <h2>Explore books</h2>
  <div>
    <img src="../assets/ColouredBooks.png" alt="colored-books" />
  </div>
</template>

<script lang="ts">
import HeaderComponent from "~/components/HeaderComponent.vue";
import SearchComponent from "~/components/SearchComponent.vue";

export default {
  name: "Index",
  components: {
    SearchComponent,
    HeaderComponent,
  },
};
</script>

<style>
div {
  margin: 10px;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
