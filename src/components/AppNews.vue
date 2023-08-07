<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <app-button @action="open">
      {{ isNewOpen ? "closed" : "open" }}
    </app-button>

    <div v-if="isNewOpen">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit,
        voluptates.
      </p>
      <app-button v-if="!wasRead" color="primary" @action="isRead">
        Read News
      </app-button>
      <app-button v-if="wasRead" color="danger" @action="reset">
        Отменить прочтение
      </app-button>
    </div>
  </div>
</template>

<script>
import AppButton from "./AppButton.vue";
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
    reset() {
      this.$emit("reset-news", this.id);
    },
  },
  components: {
    AppButton,
  },
};
</script>
