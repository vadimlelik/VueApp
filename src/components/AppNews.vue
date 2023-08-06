<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <button class="btn" @click="open">
      {{ isNewOpen ? "closed" : "open" }}
    </button>
    <p v-if="isNewOpen">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit,
      voluptates.
    </p>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    id: Number,
    isOpen: Boolean,
  },
  data() {
    return {
      isNewOpen: this.isOpen,
    };
  },
  methods: {
    open() {
      this.isNewOpen = !this.isNewOpen;
      if (this.isNewOpen) {
        this.$emit("open-news");
      }
    },
  },
};
</script>
