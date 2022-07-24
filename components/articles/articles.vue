<template>
    <div class="w-screen h-screen flex items-center justify-center">
        <div class="m-4">
            <div class="block p-6 rounded-lg shadow-lg bg-white max-w-3xl w-full">
                <div v-if="displayParagraph">
                    <div>
                        <span  class="font-medium text-lg mb-2">
                            Article : {{articleNumber}} 
                        </span>
                        <br>
                        <span class="font-medium">
                            {{currentParagraph + 1}}/{{articleLength}}
                        </span>
                    </div>
                    <div>
                        {{article.content[currentParagraph]}}
                    </div>
                    <div class="flex place-content-between mt-4">
                        <button @click="previousParagraph" type="submit" class="
                            px-6
                            py-2.5
                            bg-cyan-600
                            text-white
                            font-medium
                            text-xs
                            leading-tight
                            uppercase
                            rounded
                            shadow-md
                            hover:bg-cyan-700 hover:shadow-lg
                            focus:bg-cyan-700 focus:shadow-lg focus:outline-none focus:ring-0
                            active:bg-cyan-800 active:shadow-lg
                            transition
                            duration-150
                        ease-in-out">Prev</button>
                        <button @click="nextParagraph" type="submit" class="
                            px-6
                            py-2.5
                            bg-cyan-600
                            text-white
                            font-medium
                            text-xs
                            leading-tight
                            uppercase
                            rounded
                            shadow-md
                            hover:bg-cyan-700 hover:shadow-lg
                            focus:bg-cyan-700 focus:shadow-lg focus:outline-none focus:ring-0
                            active:bg-cyan-800 active:shadow-lg
                            transition
                            duration-150
                        ease-in-out">Next</button> 
                    </div>
                </div>
                <div v-else>
                    <div class="font-medium text-xl mb-4" align="center">
                        Quiz Time
                    </div>
                    <div>
                        <span class="font-medium">
                            Question :
                        </span>
                        {{article.quiz.question}}
                    </div>
                    <div>
                        <div class="my-1" v-for="option in article.quiz.option" :key="option.text">
                            <!-- {{option}} -->
                            <input :value='option.text' :id="option.text" v-model="quizSelect" type="radio">
                            <label :for="option.text">{{option.text}}</label>
                        </div>
                    </div>
                    <div>
                        <button @click="submitQuiz" type="submit" class="
                        w-full
                        my-1
                        px-6
                        py-2.5
                        bg-cyan-600
                        text-white
                        font-medium
                        text-xs
                        leading-tight
                        uppercase
                        rounded
                        shadow-md
                        hover:bg-cyan-700 hover:shadow-lg
                        focus:bg-cyan-700 focus:shadow-lg focus:outline-none focus:ring-0
                        active:bg-cyan-800 active:shadow-lg
                        transition
                        duration-150
                        ease-in-out">Submit</button>
                    </div>
                </div>
                
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['article', 'articleNumber'],
    data() {
        return {
            currentParagraph: 0,
            articleLength: this.article.content.length,
            displayParagraph: true,
            quizSelect: 'null',
        }
    },
    methods: {
        nextParagraph() {
            if (this.currentParagraph < this.articleLength - 1) {
                this.currentParagraph++;
            } else {
                this.displayParagraph = false;
            }
        },
        previousParagraph() {
            if (this.currentParagraph > 0) {
                this.currentParagraph--;
            }
        },
        submitQuiz() {

            if (this.quizSelect == this.article.quiz.answer) {
                // console.log('correct');
                this.$emit('incrementScore');
            } else {
                // alert('Incorrect');
                // console.log('incorrect');
            }
            this.$emit('nextArticle', this.article.quiz.answer, this.quizSelect, );
        }
    },
}   

</script>