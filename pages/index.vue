<template>
  <div class="w-screen h-screen bg-cyan-500">
    <!-- <UserDetails v-if="!applicationIntro.loginStatus && step==1" :user="user" :login="login"/>
    <MoodSelect v-if="applicationIntro.moodSelector && step==2" :user="user" :login="login"/> -->
    <div v-if="appIntro.display">
      <UserDetails v-if="appIntro.step == 1" :login="IntroStepInc"/>
      <MoodSelect v-if="appIntro.step == 2" />
    </div>
  </div>
</template>

<script>
import UserDetails from '../components/UserDetails.vue';
import MoodSelector from '../components/MoodSelect.vue';

export default {
  name: 'IndexPage',
  components: {
    UserDetails,
    MoodSelector
  },
  data() {
    return {
      appIntro : {
        display: true,
        step: 1,
      },
    };
  },
  methods: {
    IntroStepInc() {
      this.appIntro.step++;
    }
  },
  computed: {
    moodSelector() {
      return this.step == 2;
    },
    loginStatus() {
      return this.step == 3;
    }
  }
}
</script>
