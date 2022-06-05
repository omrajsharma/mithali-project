<template>
  <div class="w-screen h-screen bg-cyan-500">
    <UserDetails :user="user"/>
  </div>
</template>

<script>
import UserDetails from '../components/UserDetails.vue';

export default {
  name: 'IndexPage',
  data() {
    return {
      user: {
        name: '',
        age: '',
        email: ''
      }
    };
  }
}
</script>
