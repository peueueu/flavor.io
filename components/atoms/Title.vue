<template>
  <h1 class="title" :title="title">{{title}}</h1>
</template>

<script>
export default {
  name: "Title",
  props: {
    title: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.title {
  font-family: "Lobster", cursive;
  font-size: 7.625rem;
  letter-spacing: 0.7px;
  color: #fff;
}
</style>