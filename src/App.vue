<template>
  <div>
    <div class="container pt-1">
      <div class="card">
        <h2>Актуальные новости | {{ date }}</h2>
      </div>
      <app-news
        v-for="item in news"
        :key="item"
        :title="item.title"
        :id="item.id"
        :isOpen="item.isOpen"
      ></app-news>
    </div>
  </div>
</template>

<script>
import AppNews from "@/components/AppNews";

export default {
  name: "App",
  data() {
    return {
      date: new Date().toLocaleDateString(),
      news: [
        { title: "Первая новость", id: 1, isOpen: false },
        { title: "Вторая новость ", id: 2, isOpen: false },
        { title: "React лучше чем VUE", id: 3, isOpen: false },
      ],
    };
  },
  components: {
    "app-news": AppNews,
  },
};
</script>

<style></style>
