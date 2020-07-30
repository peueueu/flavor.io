<template>
  <input
    :id="id"
    :name="name"
    :placeholder="placeholder"
    :type="type"
    class="input-field"
    :value="search_value"
    @input="updateValue($event.target.value)"
  />
</template>

<script>
const _inputTypes = ["text", "email", "password", "checkbox"];

export default {
  name: "FlavorInput",
  data() {
    return {
      search_value: "",
    };
  },
  methods: {
    updateValue(value) {
      this.$emit("input", value);
    },
  },
  props: {
    id: {
      type: String,
    },
    name: {
      type: String,
    },
    placeholder: {
      type: String,
      default: "null",
    },
    type: {
      type: String,
      default: "text",
      validator: (value) => _inputTypes.includes(value),
    },
    value: {
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
.input-field {
  min-width: 900px;
  min-height: 55px;
  background: url("../../assets/img/search.svg"), #3b2122;
  background-repeat: no-repeat;
  font-family: "Noto Sans", sans-serif;
  background-size: 24px 24px;
  background-position: 14px 50%;
  border: 3px solid #613638;
  border-radius: 6px;
  color: #fff;
  font-weight: 200;
  padding-left: 50px;
  font-size: 1.25rem;
  &:focus {
    outline: none;
  }
  &::placeholder {
    font-style: italic;
  }
}
</style>