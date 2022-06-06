<template>
<div class="w-screen h-screen flex items-center justify-center">
    <div class="m-4">
        <div class="block p-6 rounded-lg shadow-lg bg-white max-w-md w-full">
            <div class="mb-4">
                <span class="text-lg">
                    Select Number Sequence
                </span>
                <hr>
            </div>
            <div class="flex gap-8 place-content-around mb-4 ">
                <div class="p-2 bg-fuchsia-300 rounded">
                    1. Happy
                </div>
                <div class="p-2 bg-cyan-300 rounded">
                    2. Neutral
                </div>
                <div class="p-2 bg-orange-300 rounded">
                    3. Sad
                </div>
            </div>
            <div>
                <button @click="combOne" type="submit" class="
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
                ease-in-out">1 2 3</button>

                <button @click="combTwo" type="submit" class="
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
                ease-in-out">1 3 2</button>

                
                <button @click="combThree" type="submit" class="
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
                ease-in-out">3 1 2</button>

                <button @click="combFour" type="submit" class="
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
                ease-in-out">3 2 1</button>

                <button @click="combFive" type="submit" class="
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
                ease-in-out">2 3 1</button>
                
                <button @click="combSix" type="submit" class="
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
                ease-in-out">2 1 3</button>
            </div>
        </div>
    </div>
</div>
</template>


<script>
export default {
    methods: {
        combOne () {
            this.$emit('setMoodNumber', 123)
        },
        combTwo () {
            this.$emit('setMoodNumber', 132)
        },
        combThree () {
            this.$emit('setMoodNumber', 312)
        },
        combFour () {
            this.$emit('setMoodNumber', 321)
        },
        combFive () {
            this.$emit('setMoodNumber', 231)
        },
        combSix() {
            console.log('combSix');
            this.$emit('setMoodNumber', 213)
        },
    }
}
</script>
