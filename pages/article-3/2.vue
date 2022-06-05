<template>
    <div class="w-screen h-screen flex items-center justify-center bg-cyan-500">
        <div class="block p-6 rounded-lg shadow-lg bg-white w-screen max-w-md">
            <div class="my-2">
                When I will start the app it should ask me my name, my age and gender then save it some where so later when I will analyze the eye pupil I will get the name and age of the person.
            </div>
            <NuxtLink to="/article-3/quiz-time">
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