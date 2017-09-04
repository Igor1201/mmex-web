<template>
  <div v-if='payee && !deleted'>
    <h2>{{ payee.PAYEENAME }}</h2>
    <p>{{ payee.PAYEEID }}</p>
    <button v-on:click='deleteMe'>delete</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'payee',
  props: ['payee', 'username', 'password'],
  data() {
    return { deleted: false };
  },
  methods: {
    deleteMe() {
      axios.delete(`https://vm.borges.me/payee/${this.payee.PAYEENAME}`, {
        auth: {
          username: this.username,
          password: this.password,
        },
      }).then((res) => {
        this.deleted = true;
      }).catch(console.error);
    },
  },
};
</script>

<style scoped>
h2 {
  font-weight: normal;
}
</style>
