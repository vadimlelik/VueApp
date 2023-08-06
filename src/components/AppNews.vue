<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <button class="btn" @click="open">
      {{ isNewOpen ? "closed" : "open" }}
    </button>
    <div v-if="isNewOpen">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit,
        voluptates.
      </p>
      <button v-if="!wasRead" class="btn btn-primary" @click="isRead">
        Read News
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    id: Number,
    isOpen: Boolean,
    wasRead: Boolean,
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
    isRead() {
      this.isNewOpen = false;
      this.$emit("read-news", this.id);
    },
  },
};
</script>
