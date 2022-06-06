<template>
  <div class="w-screen h-screen bg-cyan-500">
    <UserDetails v-if="!loginStatus" :user="user" :login="login"/>
  </div>
</template>

<script>
import UserDetails from '../components/UserDetails.vue';

export default {
  name: 'IndexPage',
  data() {
    return {
      user: {
        name: 'Omraj Sharma',
        age: '21',
        email: 'omraj7413@gmail.com'
      },
      loginStatus: false
    };
  },
  methods: {
    login() {
      this.loginStatus = true;
    }
  },
}
</script>
