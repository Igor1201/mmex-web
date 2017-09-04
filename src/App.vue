<template>
  <div id="app">
		<payee-list />
  </div>
</template>

<script>
import payeeList from './payee-list.vue';

export default {
  name: 'app',
  data() {
    return {};
  },
	components: { payeeList },
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
