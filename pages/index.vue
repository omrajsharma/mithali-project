<template>
  <div class="w-screen h-screen bg-cyan-500">
    <!-- INTRODUCTION -->
    <div v-if="appIntro.display">
      <UserDetails v-if="appIntro.step == 1" :login="IntroStepInc"/>
      <MoodSelect v-if="appIntro.step == 2" v-on:setMoodNumber="setMoodNum" />
      <CurrentMood v-if="appIntro.step == 3" v-on:setMoodList="setMoodList"  />
      <FirstNote v-if="appIntro.step == 4" v-on:startArticles="introFinish" />
    </div>
    <!-- END INTRODUCTION -->

    <!-- ARTICLES -->
    <div v-if="articles.displayArticle">
      <!-- <Article
      :key="articles.articleNumber"
      :article="articles.happy[articles.articleNumber-1]" 
      :articleNumber="articles.articleNumber" 
      v-on:incrementScore="incrementScore"
      v-on:nextArticle="nextArticle"
      /> -->

      <Article
        :key="articles.articleNumber"
        :article="articles.allArticles[articles.articleNumber-1]" 
        :articleNumber="articles.articleNumber" 
        v-on:incrementScore="incrementScore"
        v-on:nextArticle="nextArticle"
      />
    </div>

    <!-- CURRENT MOOD CHECKED -->
    <div v-if="articles.displayCurrentMood">
      <CurrentMood v-on:setMoodList="setMoodList"  />
    </div>

    <!-- WANT TO CONTINUE -->
    <div v-if="articles.WantToContinue">
      <WantToContinue v-on:continuePara="continuePara" v-on:stopPara="stopPara" />
    </div>

    <!-- THANK YOU -->
    <div v-if="articles.displayThankYou">
      <ThankYou/>
    </div>
  </div>
</template>

<script>
import UserDetails from '../components/UserDetails.vue';
import MoodSelector from '../components/MoodSelect.vue';
import CurrentMood from '../components/CurrentMood.vue';
import FirstNote from '../components/FirstNote.vue';
import Article from '../components/articles/articles.vue';
import WantToContinue from '~/components/articles/WantToContinue.vue';
import ThankYou from '~/components/articles/ThankYou.vue';

// IMPORT DATA
import happy from '~/data/happy.json';
import sad from '~/data/sad.json';
import neutral from '~/data/neutral.json';

export default {
  name: 'IndexPage',
  // COMPONENTS
  components: {
    UserDetails,
    MoodSelector,
    CurrentMood,
    FirstNote,
    Article,
    CurrentMood,
    WantToContinue,
    ThankYou,
    WantToContinue
},

  // DATA
  data() {
    return {
      // article data
      happyData : happy,
      sadData : sad,
      neutralData : neutral,
      // score
      score: 0,
      // intro
      appIntro : {
        display: true,
        step: 1,
      },
      // mood sequence
      moodSequence : {
        value: "",
        current: 0,
      },
      stopRead : 0,
      // mood list
      currentMoodList: [],
      articles: {
        displayThankYou: false,
        WantToContinue: false,
        displayCurrentMood: false,
        articleNumber: 1,
        displayArticle: false,
        // count
        happyCount: 0,
        sadCount: 0,
        neutralCount: 0,
        // length
        happyLength: 0,
        sadLength: 0,
        neutralLength: 0,
        // display
        happyDisplay: false,
        sadDisplay: false,
        neutralDisplay: false,
        allArticles: [],
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
      console.log('Mood Sequence Selected: ' + value);
      this.moodSequence.value = value;
      for(let i=0; i<3; i++){
        if(value[i] == 1){
          for(let a of this.happyData){
            this.articles.allArticles.push(a);
          }
        } else if( value[i] == 2){
          for(let a of this.neutralData){
            this.articles.allArticles.push(a);
          }
        } else if( value[i] == 3){
          for(let a of this.sadData){
            this.articles.allArticles.push(a);
          }
        }
      }
      // console.log(this.articles.allArticles.length);   
      this.appIntro.step++;
    },
    setMoodList(value){
      this.currentMoodList.push(value)
      if(this.articles.articleNumber > 1){
        this.displayCurrentMood = false;
        this.articles.displayArticle = true;
      }
      this.appIntro.step++;
    },
    introFinish(){
      this.appIntro.display = false;
      this.appIntro.step++;
      this.articles.displayArticle = true;
    },
    incrementScore(){
      this.score++;
      console.log('Correct Answer - score incremented. Current Score: ', this.score);
    },
    nextArticle(){
      this.articles.articleNumber++;
      if((this.articles.articleNumber-1)%3 == 0){
        this.articles.displayArticle = false;
        this.articles.displayCurrentMood = true;
      }
      if((this.articles.articleNumber-1)%5 == 0){
        console.log('inside setting want to contrinue')
        this.articles.displayArticle = false;
        this.articles.displayCurrentMood = false;
        this.articles.WantToContinue = true;
      }
      if(this.articles.articleNumber > this.articles.allArticles.length){
        this.articles.displayArticle = false;
        this.articles.displayCurrentMood = false;
        this.articles.displayThankYou = true;
      }
      console.log('next article');
    },
    continuePara() {
      console.log('inside continue para')
      this.articles.displayArticle = true;
      this.articles.displayCurrentMood = false;
      this.articles.WantToContinue = false;
    },
    stopPara() {
      this.stopRead++;
      console.log('inside stop para, stopRead:' , this.stopRead);
      this.continuePara();
    }
  },

  // LIFE CYCLE
  computed: {
    // moodSelector() {
    //   return this.step == 2;
    // },
  },

  // WATCH
  watch: {
    step(value) {
      console.log('step changed to ' + value);
    },
  },

  // MOUNTED
  mounted() {
    console.log("Finally mounted!!");
    this.articles.happyLength = this.articles.happy.length;
    this.articles.sadLength = this.articles.sad.length;
    this.articles.neutralLength = this.articles.neutral.length;
  },

}
</script>
