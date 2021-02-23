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
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
