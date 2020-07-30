<template>
  <p class="slogan__quote" :quote="quote">{{quote}}</p>
</template>

<script>
export default {
  name: "AdText",
  props: {
    quote: {
      type: String,
      default: "A journey of a thousand miles begins.",
    },
  },
};
</script>

<style>
.slogan__quote {
  font-family: "Noto Sans", sans-serif;
  color: #fff;
  font-size: 1.25rem;
  font-weight: 300;
}
</style>