<template>
  <div id="app">
    <UserBlockVue />
  </div>
</template>

<script>
import UserBlockVue from "./components/UserBlock.vue";
export default {
  name: "App",
  components: {
    UserBlockVue,
  },
};
</script>

<style lang="scss" >
#app {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
