<template>
  <div id="app">
    <Clock/>
  </div>
</template>

<script>
import Clock from "./components/ClockComp.vue";

export default {
  name: "App",
  components: {
    Clock
  }
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;

}
</style>
