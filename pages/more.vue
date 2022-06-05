<template>
    <div class="w-screen h-screen flex items-center justify-center bg-pink-400">
        <div class="block p-6 rounded-lg shadow-lg bg-white w-screen max-w-md">
            <div align="center" class="font-medium text-lg">
                Do you feel like more of these article?
            </div>
            <div class="mt-6 flex place-content-around">
                <NuxtLink to="/article-1/1">
                    <button type="submit" class="
                    px-6
                    py-2.5
                    bg-pink-600
                    text-white
                    font-medium
                    text-xs
                    leading-tight
                    uppercase
                    rounded
                    shadow-md
                    hover:bg-pink-700 hover:shadow-lg
                    focus:bg-pink-700 focus:shadow-lg focus:outline-none focus:ring-0
                    active:bg-pink-800 active:shadow-lg
                    transition
                    duration-150
                    ease-in-out">Yes</button>
                </NuxtLink>
                <NuxtLink to="/thank-you">
                    <button type="submit" class="
                    px-6
                    py-2.5
                    bg-pink-600
                    text-white
                    font-medium
                    text-xs
                    leading-tight
                    uppercase
                    rounded
                    shadow-md
                    hover:bg-pink-700 hover:shadow-lg
                    focus:bg-pink-700 focus:shadow-lg focus:outline-none focus:ring-0
                    active:bg-pink-800 active:shadow-lg
                    transition
                    duration-150
                    ease-in-out">No</button>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>