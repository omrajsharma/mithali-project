<template>
    <div class="w-screen h-screen flex items-center justify-center bg-cyan-500">
        <div class="block p-6 rounded-lg shadow-lg bg-white w-screen max-w-md">
            <div class="my-2 font-medium text-xl">
                Article 1
            </div>
            <div class="my-2">
                There are three categories i.e sad, happy, and neutral. In the beginning there are some sad covid related articles after sad there are some happy articles and some boring and weird articles.
            </div>
            <NuxtLink to="/article-1/2">
                <button type="submit" class="
                float-right
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
            </NuxtLink>
        </div>
    </div>
</template>