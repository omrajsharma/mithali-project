<template>
  <div class="w-screen h-screen bg-cyan-500">
    <!-- INTRODUCTION -->
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
      <div>
        <span>Mood sequence : </span>
        {{moodSequence}}
      </div>
    </div>
    <!-- END INTRODUCTION -->


    <!-- ARTICLES -->
    <div v-if="articles.displayArticle">
      articles
    </div>
    hey
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
      },
      moodSequence : null,
      currentMoodList: [],
      articles: {
        displayArticle: false,
        // currentMood: this.moodSequence,
        happy: [
          {
            content: [
              "JAKARTA - The world's COVID-19 deaths surpassed the five million mark on Friday, according to Reuters data. It took the world more than a year to reach the first 2.5 million COVID-19 deaths during the pandemic, but the second 2.5 million was achieved in just under eight months. An average of 8,000 deaths were reported daily worldwide in the past week, or about five deaths per minute. More than half of the global death toll in that week's average came from the United States, Russia, Brazil, Mexico and India. The total death toll in the US on Friday crossed 700,000, the highest in the world.",
              "While COVID-19 cases and hospitalizations in the US are trending down, the country's health authorities are bracing for a spike in winter when people are more active indoors. On the same day Russia reported 887 deaths, the country's highest daily figure for a year pandemic. South America is the region with the highest mortality rate in the world, accounting for 21 percent of all reported deaths. ",
              "The region is followed by North America and Eastern Europe, which each account for more than 14 percent of all deaths, according to a Reuters analysis. , the death toll in India -- one of the countries hardest hit by the Delta variant -- has dropped dramatically from an average of 4,000 per day to less than 300 when the vaccination program was launched. Delta is now the world's dominant variant of the coronavirus and has been found in 187 of the 194 member countries of the World Health Organization (WHO). ",
              "These variants have shown different vaccination rates high levels between rich and poor countries. World attention in recent days has focused on efforts to share vaccines with poor countries, where many people have not received the first dose. At the same time, people in wealthier countries are starting to be given booster doses. More than half of the world's population has not received a single dose of the COVID-19 vaccine, according to Our World in Data. ",
              "WHO said this week that for the first time the COVAX program will distribute doses only to countries with the lowest vaccination rates. The vaccine sharing program since January has allocated most of the vaccine doses to more than 140 recipient countries in proportion to the population. assistant Director-General of WHO, in a recording of last week's conference presentation uploaded to the WHO's official website."
            ],
            quiz: {
              question: '',
              option: [
                {
                  text: '789',
                  correct: false,
                },
                {
                  text: '800',
                  correct: false,
                },
                {
                  text: '889',
                  correct: false,
                },
                {
                  text: '887',
                  correct: true,
                },
              ],
            }
          }
        ],
        sad: [

        ],
        neutral:[

        ],
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
      // this.appIntro.moodNumber = value
      this.moodSequence = value;
      this.appIntro.step++;
    },
    setMoodList(value){
      this.currentMoodList.push(value)
      this.appIntro.step++;
    },
    introFinish(){
      this.appIntro.display = false;
      this.appIntro.step++;
      this.articles.displayArticle = true;
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
  },

  // WATCH
  watch: {
    step(value) {
      console.log('step changed to ' + value);
    },
  },

  // MOUNTED
  mounted() {
    console.log(this.articles);
    console.log(this.appIntro);
  },

}
</script>
