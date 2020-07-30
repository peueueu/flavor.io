<template>
  <table class="food_table">
    <thead>
      <tr class="table_header">
        <th class="food_name">Food Name</th>
        <th class="portion_amount">Portion Amount</th>
        <th class="calories">Calories</th>
        <th class="sat_fats">Saturated Fats</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="food in foodList"
        :key="food.Food_Code + food.Display_Name + (Math.random() * 1000)"
      >
        <td>{{food.Display_Name}}</td>
        <td>{{food.Portion_Amount.slice(0,4)}}/{{food.Portion_Display_Name}}</td>
        <td>{{food.Calories}}</td>
        <td>{{food.Saturated_Fats}}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "Table",
  props: {
    foodList: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>
.food_table {
  margin-top: 60px;
  max-width: 900px;
  width: 100%;
  border: 3px solid #3b2122;
  border-radius: 6px;
  border-collapse: separate;

  tr th,
  tr td {
    text-align: left;
    color: #fff;
  }
  th {
    height: 50px;
    padding: 15px;
    vertical-align: middle;
    font-weight: bold;
    text-transform: uppercase;
  }
  tbody > tr > td {
    padding: 10px 0 10px 15px;
    background: #3b2122;
    opacity: 0.59;
    border-bottom: 10px solid #553031;
  }

  tbody > tr:last-child > td {
    border-bottom: none;
  }
}
.table_header {
  background: #3b2122;
  padding: 15px;
}
.food_name {
  width: 300px;
}
.portion_amount {
  width: 250px;
}
.calories,
.sat_fats {
  width: 150px;
}
</style>