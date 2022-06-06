<template>
  <div class="w-screen h-screen bg-cyan-500">
    <div v-if="appIntro.display">
      <UserDetails v-if="appIntro.step == 1" :login="IntroStepInc"/>
      <MoodSelect v-if="appIntro.step == 2" v-on:setMoodNumber="setMoodNum" />
      <CurrentMood v-if="appIntro.step == 3" v-on:setMoodList="setMoodList"  />
      <FirstNote v-if="appIntro.step == 4" v-on:startArticles="introFinish" />
      <!-- {{currentMoodList}} -->
      <div>
        <span>AppIntro</span>
        {{appIntro}}
      </div>
      <div>
        <span>Mood List : </span>
        {{currentMoodList}}
      </div>
    </div>
  </div>
</template>

<script>
import UserDetails from '../components/UserDetails.vue';
import MoodSelector from '../components/MoodSelect.vue';
import CurrentMood from '../components/CurrentMood.vue';
import FirstNote from '../components/FirstNote.vue';

export default {
  name: 'IndexPage',
  // COMPONENTS
  components: {
    UserDetails,
    MoodSelector,
    CurrentMood,
    FirstNote,

  },

  // DATA
  data() {
    return {
      appIntro : {
        display: true,
        step: 1,
        moodNumber: 0,
      },
      currentMoodList: [],

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
    },
    setMoodList(value){
      this.currentMoodList.push(value)
      this.appIntro.step++;
    },
    introFinish(){
      this.appIntro.display = false;
      this.appIntro.step++;
    },
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
