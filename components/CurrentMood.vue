<template>
    <div class="w-screen h-screen flex items-center justify-center">
        <div class="m-4">
            <div class="block p-6 rounded-lg shadow-lg bg-white max-w-md w-full">
                <div align="center" class="mb-6 text-2xl">
                Feeling?
                </div>
                <div class="mb-6 flex justify-center gap-2 place-content-evenly">
                    <div class="text-xl">
                        <!-- 😊 -->
                        Happy
                    </div>
                    <div class="flex">
                        <!-- <span class="font-medium">
                            SAD
                        </span> -->
                        <div class="mr-2 ml-2 flex gap-4">
                            <div class="flex flex-col">
                                <label for="one">1</label>
                                <input value="1" id="one" v-model="mood" type="radio">
                            </div>
                            <div class="flex flex-col">
                                <label for="two">2</label>
                                <input value="2" id="two" v-model="mood" type="radio">
                            </div>
                            <div class="flex flex-col">
                                <label for="three">3</label>
                                <input value="3" id="three" v-model="mood" type="radio">
                            </div>
                            <div class="flex flex-col">
                                <label for="four">4</label>
                                <input value="4" id="four" v-model="mood" type="radio">
                            </div>
                            <div class="flex flex-col">
                                <label for="five">5</label>
                                <input value="5" id="five" v-model="mood" type="radio">
                            </div>
                            <div class="flex flex-col">
                                <label for="six">6</label>
                                <input value="6" id="six" v-model="mood" type="radio">
                            </div>
                            <div class="flex flex-col">
                                <label for="seven">7</label>
                                <input value="7" id="seven" v-model="mood" type="radio">
                            </div>
                            
                        </div>
                        <!-- <span class="font-medium">
                            Happy
                        </span> -->
                    </div>
                    <div class="text-xl">
                        <!-- 😔 -->
                        Sad
                    </div>
                </div>
                <div>
                    <button @click="setMood" type="submit" class="
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
</template>

<script>
export default {
    data() {
        return {
            mood: '',
        }
    },
    methods: {
        setMood(mood) {
            this.$emit('setMoodList', this.mood);
        },
    },
}
</script>