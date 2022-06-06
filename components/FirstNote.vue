<template>
    <div class="w-screen h-screen flex items-center justify-center">
        <div class="m-4">
            <div class="block p-6 rounded-lg shadow-lg bg-white max-w-md w-full">
                <div class="font-medium text-xl" align="center">
                    NOTE!
                </div>
                <p align="center" class="my-4 leading-tight">
                    After every article you need to give answer related to the article to go on next artice. <br> So read carefully!
                </p>
                <button @click="startArticle" type="submit" class="
                w-full
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
    </div>
</template>

<script>
export default {
    methods: {
        startArticle() {
            this.$emit('startArticles')
        }
    }
}
</script>