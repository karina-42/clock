<template>
  <Clock />
</template>

<script>
import Clock from './components/ClockScreen.vue';

export default {
  name: 'App',
  components: {
    Clock,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin-top: 60px;
  background-color: #000;
}
</style>
