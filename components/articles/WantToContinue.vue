<template>
    <div class="w-screen h-screen flex items-center justify-center">
        <div class="m-4">
            <div class="block p-6 rounded-lg shadow-lg bg-white max-w-md w-full">
                <div class="font-medium text-xl" align="center">
                    Do You Feel Like Reading More Of These Articles ?
                </div>
                <div class="flex place-content-between mt-4">
                        <button @click="stopPara" type="submit" class="
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
                        ease-in-out">No</button>
                        <button @click="continuePara" type="submit" class="
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
                        ease-in-out">Yes</button> 
                    </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        stopPara() {
            this.$emit('stopPara');
        },
        continuePara() {
            this.$emit('continuePara');
        }
    }
}
</script>