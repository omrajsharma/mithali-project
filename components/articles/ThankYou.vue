<template>
    <div class="w-screen h-screen flex items-center justify-center">
        <div class="m-4">
            <div class="block p-6 rounded-lg shadow-lg bg-white max-w-md w-full">
                <div class="text-2xl font-medium mb-4" align="center">
                    Thank You!
                </div>
                <button @click="goToHome" type="submit" class="
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
                ease-in-out">GO TO HOME</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        goToHome() {
            console.log(window.location)
            window.location.reload();
        }
    }
}

</script>