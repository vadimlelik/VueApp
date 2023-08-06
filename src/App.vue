<template>
  <div>
    <div class="container pt-1">
      <div class="card">
        <h2>Актуальные новости | {{ date }}</h2>
        <span>Открыто раз | {{ openRate }}</span>
      </div>
      <app-news
        v-for="item in news"
        :key="item"
        :title="item.title"
        :id="item.id"
        :isOpen="item.isOpen"
        v-on:open-news="changeRate"
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
      openRate: 0,
    };
  },
  methods: {
    changeRate() {
      this.openRate++;
    },
  },
  components: {
    "app-news": AppNews,
  },
};
</script>

<style></style>
