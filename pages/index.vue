<template>
  <div class="w-screen h-screen bg-cyan-500">
    <div v-if="appIntro.display">
      <UserDetails v-if="appIntro.step == 1" :login="IntroStepInc"/>
      <MoodSelect v-if="appIntro.step == 2" v-on:setMoodNumber="setMoodNum" />
    </div>
  </div>
</template>

<script>
import UserDetails from '../components/UserDetails.vue';
import MoodSelector from '../components/MoodSelect.vue';

export default {
  name: 'IndexPage',
  // COMPONENTS
  components: {
    UserDetails,
    MoodSelector
  },

  // DATA
  data() {
    return {
      appIntro : {
        display: true,
        step: 1,
        moodNumber: 0,
      },

    };
  },

  // METHODS
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

  // LIFE CYCLE
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
