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
              "In a world of ever larger smartphones, the Xperia 5 III shows there is another way. Boasting 5G speed, powerful performance and impressive battery life, it packs the latest Sony camera, display, sound and gaming technologies into a compact design that’s easy to use one-handed.",
              "In a world of ever larger smartphones, the Xperia 5 III shows there is another way. Boasting powerful performance and impressive battery life, it packs the latest Sony camera, display, sound and gaming technologies into a compact design that’s easy to use one-handed.",
              "The Xperia 5 III was co-developed with the engineers behind the latest Alpha 9 series cameras, renowned for their industry-leading autofocus technology, and with input from professional photographers, who helped tune the technology and refine the photographic experience and results. Key features include fast AF in all three cameras, plus object tracking technology to maintain sharp focus on moving subjects.",
              "Expand your creative possibilities with four versatile lenses in a triple camera and fast, accurate AF across all cameras. Thanks to Dual PDAF sensors, Continuous AF keeps focus on moving subjects, while Sony’s unique telephoto system supports fast AF even at extended focal lengths"
            ],
            quiz: {
              question: 'How many cameras are there in Xperia 5 III?',
              option: [
                {
                  text: '3',
                  correct: false,
                },
                {
                  text: '6',
                  correct: false,
                },
                {
                  text: '2',
                  correct: false,
                },
                {
                  text: '1',
                  correct: true,
                },
              ],
              answer: '3',
            }
          },
          // HAPPY
          {
            content: [
              "For the first time in decades, on January 19th, two incredibly rare African elephant twins have been born at Samburu National Park, part of a reserve in Northern Kenya. They are the first pair of twins to be recorded in the reserve since 2006.",
              "The birth surprised the Save The Elephants Organization, who monitors the family of elephants in the park. This is because twin births are extremely rare, forming only 1% of all elephant births.",
              "Iain Douglas-Hamilton, founder of Save the Elephants, told Newsweek: \"I have seen twins several times over my career and it's always a big event for us ... when we have had twins a couple of times before it wasn\'t a happy outcome. However, they can survive. It always causes quite a stir when they are born.\"",
              "Researchers will closely monitor the health and progress of each of the baby twin elephants, consisting of one female and one male. The twins mother, Bora, also has an older calf which was born just five years ago in 2017, which was spotted near the twins when the discovery was made."
            ],
            quiz: {
              question: 'What is the name of the twin’s mother?',
              option: [
                {
                  text: 'Yara',
                  correct: false,
                },
                {
                  text: 'Bora',
                  correct: false,
                },
                {
                  text: 'Bara',
                  correct: false,
                },
                {
                  text: 'Hara',
                  correct: true,
                },
              ],
              answer: 'Bora',
            }
          },



          // SAD
          {
            content: [
              "Germany has become the latest country to pass the sad threshold. According to figures from the country's Robert Koch Institute, 100,000 people have now died of COVID-19. Behind every number is a name, and a person",
              "A year ago, Kerstin lost her 83-year-old father to COVID-19.",
              "Kerstin lives in Düsseldorf — 600 kilometers (about 370 miles) from her parents, who were based in Berlin. Despite the virus' infectiousness and strict social distancing restrictions, the hospital called to say a final visit was possible. To Kerstin, the oldest daughter, the choice was clear.",
              "He had been taken into hospital with tuberculosis and only contracted the coronavirus later, probably from a doctor who was treating him. Now he is one of Germany's 100,000 people — according to figures from the Robert Koch Institute for Disease Control — who has since officially died from the illness. Kerstin's memories prompt laughter and tears, as she recalls her father's life and the randomness of his death.",
              "Caregivers have also suffered. Nurses have been struggling in the pandemic, seeing people being put on ventilators with their health deteriorating.\"We're all afraid of dying,\" caregiver Rita Kremers told DW. ",
              "One of her colleagues died from the virus in the ICU, she said, six weeks after infection. \"It really hits you when it's a person you knew who dies,\" she said."
            ],
            quiz: {
              question: 'Krestin was living in which city?',
              option: [
                {
                  text: 'Berlin',
                  correct: false,
                },
                {
                  text: 'Dusseldorf',
                  correct: true,
                },
                {
                  text: 'Bremen',
                  correct: false,
                },
                {
                  text: 'Weimar',
                  correct: true,
                },
              ],
              answer: 'Dusseldorf',
            }
          },
          // NEUTRAL
          {
            content: [
              "On the next-generation mobile data network, the power of 5G fast speeds changes the way you experience and share content — from super smooth gaming and streaming, to ultra-fast sharing and downloading. Upgrade to the Galaxy A52 5G and speed up your smartphone experience.",
              "Galaxy A52 5G multi-lens camera system takes photos to the next level. Go ultra high-res on the 64MP Main Camera with OIS for crisp, clear photos throughout the day. Expand the viewing angle with Ultra Wide Camera. Customise focus with Depth Camera, or get closer to the details with Macro Camera.",
              "Say bye to blurry photos and videos. OIS (Optical Image Stabilisation) helps stabilise your shots to keep motion smooth and stills crisp — even when it’s low light. The camera pulls in more light to brighten up your low light shots."
            ],
            quiz: {
              question: 'What megapixel camera we are talking in this article?',
              option: [
                {
                  text: '45MP',
                  correct: false,
                },
                {
                  text: '12MP',
                  correct: false,
                },
                {
                  text: '64MP',
                  correct: false,
                },
                {
                  text: '42',
                  correct: true,
                },
              ],
              answer: '64MP',
            }
          },
          // HAPPY
          {
            content: [
              "On the 6th of December, the Welsh Government announced plans to offer every household in the country a free tree to plant, in a bid to tackle climate change.",
              "In collaboration with the Woodland Trust, the new policy will give people the chance to choose a tree of their own to plant, or to instead have a tree planted on their behalf, as not all households will be able to plant one themselves. These households will have the option for their tree to be planted in the location of their choice within a wide area of options across the country.",
              "The first trees will be available to collect from March, 2022, from several community hubs located across the country. Up to 20 extra hubs are also planned to be up and running by the month of October, which will help to boost the campaigns momentum and make collection much more accessible for the public.",
              "“Trees are amazing - they save lives by keeping our air clean, they improve people's physical and mental health, they are essential for tackling our nature emergency, improving biodiversity and, of course, in tackling climate change.” the Deputy Minister said.",
              "The campaign will also build on efforts to build a National Forest for Wales, with the Deputy Minister also revealing that a consultation would be launched in early 2022 regarding the matter."
            ],
            quiz: {
              question: 'On which date, the Welsh Government announced plans to offer every household in the country a free tree to plant, in a bid to tackle climate change.',
              option: [
                {
                  text: '8th December',
                  correct: false,
                },
                {
                  text: '9th December ',
                  correct: false,
                },
                {
                  text: '28th December ',
                  correct: false,
                },
                {
                  text: '6th December ',
                  correct: true,
                },
              ],
              answer: '6th December ',
            }
          },


          // SAD
          {
            content: [
              "COVID, death and mourning in Germany: 'No one should have to die alone'People have been dying lonely deaths in nursing homes and hospitals around Germany due to coronavirus pandemic and restrictions on close contact. It has been devastating for those they leave behind.",
              "We weren't allowed to ride in the ambulance with him or enter the hospital. We couldn't talk to his doctors. It was horrific,\" says Silke Kleibömer, recalling the day her father was rushed to the hospital — April 28, his birthday. He was \"terrified,\" says his daughter, \"he knew his life was coming to an end.",
              "Hans-Jürgen had a pulmonary disease and had been on oxygen for years. He was doing so poorly that the family called paramedics. He died in the hospital's intensive care unit (ICU) just seven days later.",
              "During the first phase of the coronavirus pandemic hospitals and nursing homes imposed restrictions and bans on outside contact. After a loosening of rules over the summer, they are once again getting stricter as infection rates rise. State and federal governments say they are committed to protecting at-risk individuals in hospitals and nursing homes.",
              "Rapid testing is to be implemented to facilitate visiting regulations, as restrictions don't just affect COVID-19 patients. They also affect people like Silke Kleibömer's father Heinz-Jürgen.",
              "In the hospital, doctors found that he had pneumonia. Silke Kleibömer says it was impossible to talk with her father on the telephone. \"We called him every day, for about 10 or 20 seconds,\" she says — after that he was out of breath. \"Anyone who has ever suffered shortness of breath knows that it's deadly terrifying,\" she adds.",
              "'He didn't want to go'. When Silke's mother called the hospital to find out what the family should expect, she was harangued by a doctor who yelled at her that they didn't have the time to talk with every relative who called. When the father was moved  into intensive care, no one bothered to inform the family. Silke Kleibömer, who runs an outpatient nursing service herself, says she can't understand such attitudes: \"Then you have to delegate. We're just talking about making time for a phone call here.",
            ],
            quiz: {
              question: 'According to the article, When was her father rushed to the hospital?',
              option: [
                {
                  text: '23RD APRIL',
                  correct: false,
                },
                {
                  text: '27TH APRIL',
                  correct: true,
                },
                {
                  text: '28TH APRIL',
                  correct: false,
                },
                {
                  text: '30RD APRIL',
                  correct: true,
                },
              ],
              answer: '28TH APRIL',
            }
          },
          // NEUTRAL
          {
            content: [
              "Cotton is a soft, fluffy staple fiber that grows in a boll, or protective case, around the seeds of the cotton plants of the genus Gossypium in the mallow family Malvaceae. The fiber is almost pure cellulose, and can contain minor percentages of waxes, fats, pectins, and water. Under natural conditions, the cotton bolls will increase the dispersal of the seeds.",
              "The plant is a shrub native to tropical and subtropical regions around the world, including the Americas, Africa, Egypt and India. The greatest diversity of wild cotton species is found in Mexico, followed by Australia and Africa. Cotton was independently domesticated in the Old and New Worlds.",
              "The fiber is most often spun into yarn or thread and used to make a soft, breathable, and durable textile. The use of cotton for fabric is known to date to prehistoric times; fragments of cotton fabric dated to the fifth millennium BC have been found in the Indus Valley Civilization, as well as fabric remnants dated back to 6000 BC in Peru. Although cultivated since antiquity, it was the invention of the cotton gin that lowered the cost of production that led to its widespread use, and it is the most widely used natural fiber cloth in clothing today.",
              "Current estimates for world production are about 25 million tonnes or 110 million bales annually, accounting for 2.5% of the world's arable land. India is the world's largest producer of cotton. The United States has been the largest exporter for many years."
            ],
            quiz: {
              question: 'The greatest diversity of wild cotton species is found in Mexico, followed by Australia and Africa.',
              option: [
                {
                  text: 'True',
                  correct: false,
                },
                {
                  text: 'False',
                  correct: false,
                },
              ],
              answer: 'True',
            }
          },
          // HAPPY
          {
            content: [
              "An 84 year old former farmer, soldier, and shopkeeper from Puebla Mexico, is about to graduate from an engineering and industrial management program at the Meritorious Autonomous University of Puebla (BUAP). Despite the university being one of the most prestigious and competitive in Puebla, Felipe Espinosa Tecuapetla easily managed to pass the entrance exams when he enrolled at age 79.",
              "His journey has been challenging, however he never gave up on his lifelong dream of getting his engineering degree. Apart from continuing working at the local market selling vegetables, he wakes up everyday at 4:30am to catch two buses to make it in time for class.",
              "Felipe does state that his main challenge was to afford a laptop and learn how to use it, since he had never had one before; yet, he was determined to achieve his dream. Eventually he managed to buy one, and taught himself how to use it.",
              "In addition to achieving his dream, Felipe wanted to prove to the world that age has nothing to do with learning and that it’s all about mastering one’s mind. To further prove his point and go beyond his dreams, he is now planning on continuing his education and getting a masters degree."
            ],
            quiz: {
              question: 'How old was he when he managed to pass the entrance exam?',
              option: [
                {
                  text: '84 year old',
                  correct: false,
                },
                {
                  text: '78 year old',
                  correct: false,
                },
                {
                  text: '77 year old',
                  correct: false,
                },
                {
                  text: '79 year old ',
                  correct: true,
                },
              ],
              answer: '79 year old ',
            }
          },


          // SAD
          {
            content: [
              "Nearly 80,000 people have died of COVID-19 since the coronavirus pandemic hit Germany. Behind every statistic lies a sad personal story about the fates of individuals and their families.",
              "One terrible thing about COVID-19 is not just that people are dying of it, but the circumstances in which they die. A COVID-19 death often occurs in isolation, behind closed doors. How can we cope with this? Reporters Nicola Albrecht and Susann von Lojewski examine how COVID-19 has changed our experience of death. ",
              "They speak to people who have lost loved ones, such as Manu, who lost his fiancée Brittanya to COVID-19 - she was just 29. Posting on Instagram from her sickbed, rapper Brittanya gave herself and her fans confidence to fight the battle against the virus. She died a few days later. Ralf Brepohl lost his mother and has been asking himself ever since whether he was the one who infected her. ",
              "He says that he would never forgive himself. Often, intensive care workers are the last people allowed to accompany patients who are sick and dying of COVID-19. And even if they are now used to it, COVID-19 is pushing them to the limit. Nurse Celine Pinkau from Senftenberg describes the moment she had to put a patient she’d grown fond of into a clinically sealed body bag. ",
              "Hospital chaplains like Stefan Pfeifer are not always able to comfort bereaved family members. He is worried that being unable to say goodbye to their loved ones will take a major emotional toll on them. The film shows how COVID-19 has brutally disrupted our death rituals and asks how we can give as much dignity as possible to the dying, also in the time of the coronavirus.",
            ],
            quiz: {
              question: 'According to the article, Manu lost his fiancée. What was her name?',
              option: [
                {
                  text: 'Rita',
                  correct: false,
                },
                {
                  text: 'Joanna',
                  correct: true,
                },
                {
                  text: 'Brittanya',
                  correct: false,
                },
                {
                  text: 'Valeria',
                  correct: true,
                },
              ],
              answer: 'Brittanya',
            }
          },
          // NEUTRAL
          {
            content: [
              "A grinder-mixer is a type of agricultural machine used to process livestock feed from grain. A grinder-mixer is a portable mill that combines the mixing and grinding operations.Grinding of ingredients generally improves feed digestibility, acceptability, mixing properties and pelletability.",
              "Grain is typically pulverized in a grinder-mixer either by hammer mills or roller mills.Hammermills are impact grinders with swinging or stationary steel bars forcing ingredients against a circular screen or solid serrated section designated as a striking plate. Material is held in the grinding chamber until it is reduced to the size of the openings in the screen. The number of hammers on a rotating shaft, their size, arrangement, sharpness, the speed of rotation, wear patterns, and clearance at the tip relative to the screen or striking plate are important variables in grinding capacity and the appearance of ground feed. ",
              "A combination of cutting, attrition, and crushing occurs in roller mills. These are smooth or corrugated rolls rotating at the same speed set at a pre-determined distance apart with material passing between the two. A tearing action may be added by operating the rolls at different speeds and by different for each roll. ",
              "The objective of feed mixing is to start with a certain assortment of ingredients called a \"formula\", totaling some definite weight. This is processed so that each small unit of the whole, either a mouthful or a day's feeding, is the same proportion as the original formula. The mixing process is done in the vertical tank. It determines the balanced nutritional quality of the feed. ",
              "After the feed is ground and mixed, it passes through a system of particulate screens. From there, only suitable granules pass on to the delivery process, and waste is sent to the charging chute. Mizer grinder is an electronic kitchen appliance that used to mix and grind various food items. It is compact on size and plays a major role in preparation of food. It usually comes with three jars crafted out of high quality stainless steel. These jars are incorporated with multifunctional blades that can perform all sorts of chores in a few seconds."
            ],
            quiz: {
              question: 'Mizer grinder is an electronic kitchen appliance that used to mix and grind various food items?',
              option: [
                {
                  text: 'True',
                  correct: false,
                },
                {
                  text: 'False',
                  correct: false,
                },
              ],
              answer: 'True',
            }
          },
          // HAPPY
          {
            content: [
              "Madrid, the capital city of Spain, is planning to build a 75km ‘green wall’ made of around half a million trees. It is hoped the wall will help to combat air pollution in the city and combat climate change",
              "Once completed, Madrid's green wall will transform into a forest of indigenous trees, that will have the ability to absorb heat generated by human activity in the city,  as well as combat the ‘heat island effect’, by absorbing up to 175,000 tons of CO2 per year.",
              "The construction of this flourishing ‘green wall’ is forecast to decrease temperatures under the shade by up to 2 degrees, according to Mariano Fuentes, Madrid's councillor for the environment. This may help to provide some respite for animals during the summer months.",
              "As part of the initiative, the government of Madrid is also restricting private car use in certain urban centres, creating ‘environmental corridors’ in every district, promoting cycling, the use of public transport, implementing sustainable sources of energy, and creating a green culture among its citizens.",
              "Madrid's green wall will be unique in the sense that it will be preserved with a minimum effort so it can be sustainable over time, unlike with parks or green areas in most cities. With desertification being a growing issue in Spain, the government is prioritizing making its cities and urban areas more eco-friendly to better adapt to climate change.",

            ],
            quiz: {
              question: 'According to the article, The construction of this flourishing ‘green wall’ is forecast to decrease temperatures under the shade by up to 6 degrees?',
              option: [
                {
                  text: 'True',
                  correct: false,
                },
                {
                  text: 'False',
                  correct: false,
                },
              ],
              answer: 'False',
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
      // console.log(this.articles.allArticles);   
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
      this.stopRead++;
      // this.articles.displayArticle = false;
      // this.articles.displayCurrentMood = false;
      // this.articles.WantToContinue = false;
      // this.articles.displayThankYou = true;
      this.articles.displayArticle = true;
      this.articles.displayCurrentMood = false;
      this.articles.WantToContinue = false;
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
