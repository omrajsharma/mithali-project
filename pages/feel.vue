<template>
    <div class="w-screen h-screen flex items-center justify-center bg-cyan-500">
        <div class="block p-6 rounded-lg shadow-lg bg-white w-screen max-w-md">
            <div align="center" class="mb-6 text-2xl">
                Feeling?
            </div>
            <div class="mb-6 flex justify-center gap-4 place-content-evenly">
                <div class="text-2xl">
                    😔
                </div>
                <div class="flex">
                    <span class="font-medium">
                        SAD
                    </span>
                    <div class="mr-8 ml-8 flex gap-4">
                        <div class="flex flex-col">
                            <label for="">1</label>
                            <input type="radio">
                        </div>
                        <div class="flex flex-col">
                            <label for="">2</label>
                            <input type="radio">
                        </div>
                        <div class="flex flex-col">
                            <label for="">3</label>
                            <input type="radio">
                        </div>
                        <div class="flex flex-col">
                            <label for="">4</label>
                            <input type="radio">
                        </div>
                        <div class="flex flex-col">
                            <label for="">5</label>
                            <input type="radio">
                        </div>
                    </div>
                    <span class="font-medium">
                        Happy
                    </span>
                </div>
                <div class="text-2xl">
                    😊
                </div>
            </div>
            <NuxtLink to="/article-4/1">
                <button type="submit" class="
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
                ease-in-out">Submit</button>
            </NuxtLink>
        </div>
    </div>
</template>