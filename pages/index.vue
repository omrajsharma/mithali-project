<template>
  <div class="w-screen h-screen bg-cyan-500">
    <!-- INTRODUCTION -->
    <div v-if="appIntro.display">
      <UserDetails v-if="appIntro.step == 1" :login="IntroStepInc"/>
      <MoodSelect v-if="appIntro.step == 2" v-on:setMoodNumber="setMoodNum" />
      <CurrentMood v-if="appIntro.step == 3" v-on:setMoodList="setMoodList"  />
      <FirstNote v-if="appIntro.step == 4" v-on:startArticles="introFinish" />
      <div>
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
        <div>
          <span>score : </span>
          {{score}}
        </div>
      </div>
    </div>
    <!-- END INTRODUCTION -->

    <!-- ARTICLES -->
    <div v-if="articles.displayArticle">
      <Article
      :key="articles.articleNumber"
      :article="articles.happy[articles.articleNumber-1]" 
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
      score: 0,
      appIntro : {
        display: true,
        step: 1,
      },
      moodSequence : {
        value: "",
        current: 0,
      },

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
        happy: [
          // SAD
          {
            content: [
              "JAKARTA - The world's COVID-19 deaths surpassed the five million mark on Friday, according to Reuters data. It took the world more than a year to reach the first 2.5 million COVID-19 deaths during the pandemic, but the second 2.5 million was achieved in just under eight months. An average of 8,000 deaths were reported daily worldwide in the past week, or about five deaths per minute. More than half of the global death toll in that week's average came from the United States, Russia, Brazil, Mexico and India. The total death toll in the US on Friday crossed 700,000, the highest in the world.",
              "While COVID-19 cases and hospitalizations in the US are trending down, the country's health authorities are bracing for a spike in winter when people are more active indoors. On the same day Russia reported 887 deaths, the country's highest daily figure for a year pandemic. South America is the region with the highest mortality rate in the world, accounting for 21 percent of all reported deaths. ",
              "The region is followed by North America and Eastern Europe, which each account for more than 14 percent of all deaths, according to a Reuters analysis. , the death toll in India -- one of the countries hardest hit by the Delta variant -- has dropped dramatically from an average of 4,000 per day to less than 300 when the vaccination program was launched. Delta is now the world's dominant variant of the coronavirus and has been found in 187 of the 194 member countries of the World Health Organization (WHO). ",
              "These variants have shown different vaccination rates high levels between rich and poor countries. World attention in recent days has focused on efforts to share vaccines with poor countries, where many people have not received the first dose. At the same time, people in wealthier countries are starting to be given booster doses. More than half of the world's population has not received a single dose of the COVID-19 vaccine, according to Our World in Data. ",
              "WHO said this week that for the first time the COVAX program will distribute doses only to countries with the lowest vaccination rates. The vaccine sharing program since January has allocated most of the vaccine doses to more than 140 recipient countries in proportion to the population. assistant Director-General of WHO, in a recording of last week's conference presentation uploaded to the WHO's official website."
            ],
            quiz: {
              question: 'According to the article, Russia recorded how many cases?',
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
              answer: '887',
            }
          },
          // NEUTRAL
          {
            content: [
              "Over the last two weeks, COVID-19 cases in Tunisia have increased by 138% to hit all-time highs, according to Our World in Data. Friday, Tunisia reported 9,823 new cases and 134 new deaths Thursday, per WHO data.",
              "The North African country of 12 million people has a total caseload of more than 464,000 cases — and rapidly increasing, reported Al Jazeera.",
              "“We are in a catastrophic situation,” Nisaf Ben Alaya, a Tunisia health ministry spokesperson, said, per Al Jazeera. “The health system collapsed.",
              "“We are struggling to provide oxygen. … Doctors are suffering from unprecedented fatigue,” she said to Al Jazeera.",
              "The country has reimposed a total lockdown across most of the country and a partial lockdown on the capital, according to Al Jazeera. So far, only 4% of the population has received a coronavirus vaccination.",
            ],
            quiz: {
              question: 'According to the article, How many deaths Tunisia recorded on Thursday?',
              option: [
                {
                  text: '9823',
                  correct: false,
                },
                {
                  text: '9582',
                  correct: false,
                },
                {
                  text: '10000',
                  correct: false,
                },
                {
                  text: '9888',
                  correct: true,
                },
              ],
              answer: '9823',
            }
          },
          // HAPPY
          {
            content: [
              "The Nature Conservancy is planning to transform six abandoned coal mines in south-west Virginia into ‘solar hubs’, according to the Washington Post. Once completed, they will be able to provide suffice amounts of energy to the electric grid.",
              "Across the region, there are several hundreds of square miles of previously cleared mine lands, over 100,000 acres, according to an analysis by Downstream Strategies. And that’s in only the west of Virginia. Many locations in the state of Nevada are also prime candidates for future solar expansion, with over a million acres of minefields and brownfield sites ripe for the picking.",
              "The organisation hopes there can be further nationwide expansion in the future in addition to the six coal mines they already own. Many of the mines in the area also have existing road and power-line infrastructure, making many of them suitable candidates for further solar expansion in the future.",
              "Daniel Kestner, from the Virginia Department of Energy, is hopeful that the solar projects will bring new jobs to the area alongside tax revenue, a win-win for both citizens in the area and green energy expansion."
            ],
            quiz: {
              question: 'How many coal mines are present in south-west Virginia?',
              option: [
                {
                  text: '4',
                  correct: false,
                },
                {
                  text: '6',
                  correct: false,
                },
                {
                  text: '8',
                  correct: false,
                },
                {
                  text: '10',
                  correct: true,
                },
              ],
              answer: '6',
            }
          },
          // SAD
          {
            content: [
              "JAKARTA - The world's COVID-19 deaths surpassed the five million mark on Friday, according to Reuters data. It took the world more than a year to reach the first 2.5 million COVID-19 deaths during the pandemic, but the second 2.5 million was achieved in just under eight months. An average of 8,000 deaths were reported daily worldwide in the past week, or about five deaths per minute. More than half of the global death toll in that week's average came from the United States, Russia, Brazil, Mexico and India. The total death toll in the US on Friday crossed 700,000, the highest in the world.",
              "While COVID-19 cases and hospitalizations in the US are trending down, the country's health authorities are bracing for a spike in winter when people are more active indoors. On the same day Russia reported 887 deaths, the country's highest daily figure for a year pandemic. South America is the region with the highest mortality rate in the world, accounting for 21 percent of all reported deaths. ",
              "The region is followed by North America and Eastern Europe, which each account for more than 14 percent of all deaths, according to a Reuters analysis. , the death toll in India -- one of the countries hardest hit by the Delta variant -- has dropped dramatically from an average of 4,000 per day to less than 300 when the vaccination program was launched. Delta is now the world's dominant variant of the coronavirus and has been found in 187 of the 194 member countries of the World Health Organization (WHO). ",
              "These variants have shown different vaccination rates high levels between rich and poor countries. World attention in recent days has focused on efforts to share vaccines with poor countries, where many people have not received the first dose. At the same time, people in wealthier countries are starting to be given booster doses. More than half of the world's population has not received a single dose of the COVID-19 vaccine, according to Our World in Data. ",
              "WHO said this week that for the first time the COVAX program will distribute doses only to countries with the lowest vaccination rates. The vaccine sharing program since January has allocated most of the vaccine doses to more than 140 recipient countries in proportion to the population. assistant Director-General of WHO, in a recording of last week's conference presentation uploaded to the WHO's official website."
            ],
            quiz: {
              question: 'According to the article, Russia recorded how many cases?',
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
              answer: '887',
            }
          },
          // NEUTRAL
          {
            content: [
              "Over the last two weeks, COVID-19 cases in Tunisia have increased by 138% to hit all-time highs, according to Our World in Data. Friday, Tunisia reported 9,823 new cases and 134 new deaths Thursday, per WHO data.",
              "The North African country of 12 million people has a total caseload of more than 464,000 cases — and rapidly increasing, reported Al Jazeera.",
              "“We are in a catastrophic situation,” Nisaf Ben Alaya, a Tunisia health ministry spokesperson, said, per Al Jazeera. “The health system collapsed.",
              "“We are struggling to provide oxygen. … Doctors are suffering from unprecedented fatigue,” she said to Al Jazeera.",
              "The country has reimposed a total lockdown across most of the country and a partial lockdown on the capital, according to Al Jazeera. So far, only 4% of the population has received a coronavirus vaccination.",
            ],
            quiz: {
              question: 'According to the article, How many deaths Tunisia recorded on Thursday?',
              option: [
                {
                  text: '9823',
                  correct: false,
                },
                {
                  text: '9582',
                  correct: false,
                },
                {
                  text: '10000',
                  correct: false,
                },
                {
                  text: '9888',
                  correct: true,
                },
              ],
              answer: '9823',
            }
          },
          // HAPPY
          {
            content: [
              "The Nature Conservancy is planning to transform six abandoned coal mines in south-west Virginia into ‘solar hubs’, according to the Washington Post. Once completed, they will be able to provide suffice amounts of energy to the electric grid.",
              "Across the region, there are several hundreds of square miles of previously cleared mine lands, over 100,000 acres, according to an analysis by Downstream Strategies. And that’s in only the west of Virginia. Many locations in the state of Nevada are also prime candidates for future solar expansion, with over a million acres of minefields and brownfield sites ripe for the picking.",
              "The organisation hopes there can be further nationwide expansion in the future in addition to the six coal mines they already own. Many of the mines in the area also have existing road and power-line infrastructure, making many of them suitable candidates for further solar expansion in the future.",
              "Daniel Kestner, from the Virginia Department of Energy, is hopeful that the solar projects will bring new jobs to the area alongside tax revenue, a win-win for both citizens in the area and green energy expansion."
            ],
            quiz: {
              question: 'How many coal mines are present in south-west Virginia?',
              option: [
                {
                  text: '4',
                  correct: false,
                },
                {
                  text: '6',
                  correct: false,
                },
                {
                  text: '8',
                  correct: false,
                },
                {
                  text: '10',
                  correct: true,
                },
              ],
              answer: '6',
            }
          },
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
      this.moodSequence.value = value;
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
      console.log('score incremented')
      this.score++;
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
      if(this.articles.articleNumber > this.articles.happy.length){
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
      console.log('inside stop para')
      this.articles.displayArticle = false;
      this.articles.displayCurrentMood = false;
      this.articles.WantToContinue = false;
      this.articles.displayThankYou = true;
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
    console.log(this.articles);
    console.log(this.appIntro);
    console.log(this.moodSequence);
    this.articles.happyLength = this.articles.happy.length;
    this.articles.sadLength = this.articles.sad.length;
    this.articles.neutralLength = this.articles.neutral.length;
  },

}
</script>
