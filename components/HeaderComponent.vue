<template>
  <header>
    <h1>{{ title }}</h1>
    <NuxtLink :to="`/`" class="header-link">Go Home</NuxtLink>
  </header>
</template>

<script lang="ts">
export default {
  name: "HeaderComponent",
  props: {
    title: String,
  },
};
</script>

<style scoped>
header {
  display: flex;
  /* justify-content: space-between; */
  align-items: center;
  margin-bottom: 20px;
}
.header-link {
  color: black;
  border: 2px solid purple;
  border-radius: 3px;
  padding: 5px;
  text-decoration: none;
  width: fit-content;
  font-size: 16px;
}
</style>
