<template>
  <div>
    <div class="container pt-1">
      <div class="card">
        <h2>Актуальные новости | {{ date }}</h2>
        <span
          >Открыто раз | {{ openRate }} | Прочитано
          <strong>{{ readRate }} </strong>
        </span>
      </div>
      <app-news
        v-for="item in news"
        :key="item"
        :title="item.title"
        :id="item.id"
        :isOpen="item.isOpen"
        :wasRead="item.wasRead"
        v-on:open-news="changeRate"
        @read-news="readNews"
        @reset-news="resetNews"
      ></app-news>
    </div>
  </div>
</template>

<script>
import AppNews from "@/components/AppNews";

export default {
  name: "App",
  emits: {
    "read-news"(id) {
      if (!id) {
        console.log("No is id");
      }
    },
  },
  data() {
    return {
      date: new Date().toLocaleDateString(),
      news: [
        { title: "Первая новость", id: 1, isOpen: false, wasRead: false },
        { title: "Вторая новость ", id: 2, isOpen: false, wasRead: false },
        { title: "React лучше чем VUE", id: 3, isOpen: false, wasRead: false },
      ],
      readRate: 0,
      openRate: 0,
    };
  },
  methods: {
    changeRate() {
      this.openRate++;
    },
    readNews(id) {
      const indexNews = this.news.findIndex((item) => item.id === id);
      this.news[indexNews].wasRead = true;
      this.readRate++;
    },
    resetNews(id) {
      console.log(id, "id");

      const indexNews = this.news.findIndex((item) => item.id === id);
      this.news[indexNews].wasRead = false;
      this.readRate--;
    },
  },
  components: {
    "app-news": AppNews,
  },
};
</script>

<style></style>
