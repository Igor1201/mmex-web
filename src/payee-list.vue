<template>
  <div>
    <input v-model='username' />
    <input type='password' v-model='password' />
    <button v-on:click='doRequest'>Login</button>

		<payee v-for='payee in payees'
					 :key='payee.PAYEEID'
					 :payee='payee'
					 :username='username'
					 :password='password' />
  </div>
</template>

<script>
import axios from 'axios';
import payee from './payee.vue';

export default {
  name: 'payee-list',
  data() {
    return {
      username: 'a',
      password: 'a',
      payees: [],
    };
  },
  methods: {
    doRequest() {
      axios.get('https://vm.borges.me/payee', {
        auth: {
          username: this.username,
          password: this.password,
        },
      }).then((res) => {
        this.payees = res.data;
      }).catch(console.error);
    },
  },
	components: { payee },
};
</script>
