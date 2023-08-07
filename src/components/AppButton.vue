<template>
  <button class="btn" :class="color" @click="$emit('action')">
    <slot />
  </button>
</template>

<script>
export default {
  emit: ["action"],
  props: {
    color: {
      type: String,
      required: true,
      validator(value) {
        return ["", "primary", "danger"].includes(value);
      },
    },
  },
  data() {
    return {};
  },
  methods() {},
};
</script>

<style></style>
