<template>
  <div class="table_container">
    <FlavorInput placeholder="Search Food..." v-model="search" />
    <Table :foodList="displayedFoods" />
    <!-- <TableButton :offset="offset" /> -->
    <transition name="fade">
      <div class="page_control" v-if="search == ''">
        <button
          class="btn"
          @click="offset -= 10"
          :disabled="!hasPrevPage"
          :style="{opacity: !hasPrevPage ? '.6' : '1', cursor: !hasPrevPage ? 'not-allowed' : 'pointer'}"
        >Previous</button>
        <button
          class="btn"
          @click="offset += 10"
          :disabled="!hasNextPage"
          :style="{opacity: !hasNextPage ? '.6' : '1', cursor: !hasNextPage ? 'not-allowed' : 'pointer'}"
        >Next</button>
      </div>
    </transition>
  </div>
</template>

<script>
let file = require("../../api/food_api.json");
import FlavorInput from "../atoms/FlavorInput";
import Table from "../molecules/Table";

export default {
  name: "FlavorTable",
  components: {
    FlavorInput,
    Table,
  },
  data() {
    return {
      foods: "",
      search: "",
      pageInitial: 0,
      offset: 0,
      limit: 10,
    };
  },
  methods: {
    getData() {
      let data = [...file];
      this.foods = data;
    },
  },
  created() {
    this.getData();
  },
  computed: {
    displayedFoods() {
      let foodDisplay =
        this.search == ""
          ? this.filteredFoods.slice(this.offset, this.limit + this.offset)
          : this.filteredFoods.slice(
              this.pageInitial,
              this.limit + this.pageInitial
            );
      console.log(
        this.filteredFoods.slice(
          this.pageInitial,
          this.limit + this.pageInitial
        ).length
      );
      console.log(this.offset);
      return foodDisplay;
    },
    hasNextPage() {
      const nextOffset = this.offset + 10;
      return Boolean(
        this.filteredFoods.slice(nextOffset, this.limit + nextOffset).length
      );
    },
    hasPrevPage() {
      const prevOffset = this.offset - 10;
      return Boolean(
        this.filteredFoods.slice(prevOffset, this.limit + prevOffset).length
      );
    },
    filteredFoods() {
      return this.foods.filter((food) => {
        return food.Display_Name.toLowerCase().match(
          this.search.toLowerCase().trim()
        );
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.page_control {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
  .btn {
    margin-right: 40px;
    cursor: pointer;
    font-family: "Noto Sans";
    background: #3b2122;
    color: #f2f2f2;
    font-weight: 700;
    text-transform: uppercase;
    border: none;
    border-radius: 6px;
    padding: 10px;
    &:hover {
      background: #c76f72;
    }
    &:focus {
      outline: none;
    }
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.6s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translate3d(-30vw, 0, 0);
}
</style>