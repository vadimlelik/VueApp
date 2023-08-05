<template>
  <div>

    <div class="container pt-1">
      <div class="card">
        <h2>Актуальные новости | {{ date }}</h2>
      </div>
      <app-news
          v-for="item in news"
          :key="item"
          :title='item'
      ></app-news>
    </div>
  </div>
</template>

<script>

import AppNews from "@/components/AppNews";

export default {
  name: 'App',
  data() {
    return {
      date: new Date().toLocaleDateString(),
      news: ['Первая новость', 'Вторая новость ', 'React лучше чем VUE'],
    }
  },
  components: {
    'app-news': AppNews
  }
}
</script>

<style>

</style>
