<template>
  <div class="w-screen h-screen bg-cyan-500">
    <!-- <UserDetails v-if="!applicationIntro.loginStatus && step==1" :user="user" :login="login"/>
    <MoodSelect v-if="applicationIntro.moodSelector && step==2" :user="user" :login="login"/> -->
    <div v-if="appIntro.display">
      <UserDetails v-if="appIntro.step == 1" :login="IntroStepInc"/>
      <MoodSelect v-if="appIntro.step == 2" v-on:setMoodNumber="setMoodNum" />
      {{appIntro.moodNumber}} {{fromChild}}
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
        moodNumber: 0,
      },
      fromChild: '',
    };
  },
  methods: {
    IntroStepInc() {
      this.appIntro.step++;
    },
    MoodNumber(){
      console.log('testing')
    },
    setMoodNum(value){
      console.log('inside parent')
      this.appIntro.moodNumber = value
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
