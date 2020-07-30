<template>
  <div class="container">
    <LogoWrapper />
    <FlavorTable />
  </div>
</template>

<script>
import LogoWrapper from "../components/molecules/LogoWrapper";
import FlavorTable from "../components/organisms/FlavorTable";
export default {
  components: {
    LogoWrapper,
    FlavorTable,
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  height: 100vh;
}
</style>
