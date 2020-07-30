<template>
  <div class="main_container">
    <Logo />
    <div class="company_container">
      <Title title="Flavor.io" />
      <Slogan />
    </div>
  </div>
</template>

<script>
import Title from "../atoms/Title";
import Slogan from "../atoms/Slogan";
import Logo from "../atoms/Logo";
export default {
  name: "LogoWrapper",
  components: {},
};
</script>

<style lang="scss" scoped>
.main_container {
  display: flex;
  align-items: center;
  margin: 40px 0 60px;
  .company_container {
    margin-left: 40px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>