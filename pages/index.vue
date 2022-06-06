<template>
  <div class="w-screen h-screen bg-cyan-500">
    <UserDetails v-if="!loginStatus && step==1" :user="user" :login="login"/>
    <MoodSelect v-if="moodSelector && step==2" :user="user" :login="login"/>
  </div>
</template>

<script>
import UserDetails from '../components/UserDetails.vue';
import MoodSelector from '../components/MoodSelect.vue';

export default {
  name: 'IndexPage',
  data() {
    return {
      user: {
        name: 'Omraj Sharma',
        age: '21',
        email: 'omraj7413@gmail.com'
      },
      step: 1,
      loginStatus: false,
      moodSelector: true,
    };
  },
  methods: {
    login() {
      this.loginStatus = true;
      this.step++;
    }
  },
}
</script>
