<template>
  <ul>
    <li v-for="item in lists" :key="item">{{ item }}</li>
  </ul>
</template>

<script>
export default {
  inject: ["lists"],
};
</script>

<style></style>
