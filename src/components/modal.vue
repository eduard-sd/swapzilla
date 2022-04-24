<template>
  <div class="hello">
    <v-snackbar v-model="isOpen" :vertical="true" />
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    open() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>
<style scoped></style>
