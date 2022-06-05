<template>
    <div class="w-screen h-screen flex items-center justify-center bg-cyan-500">
        <div class="block p-6 rounded-lg shadow-lg bg-white w-screen max-w-md">
            <div class="my-2 font-medium text-xl" align="center">
                Quiz Time
            </div>
            <div class="my-2">
                <span class="font-medium">
                    Question : 
                </span>
                According to the article how many deaths reported in the past week?
            </div>
            <div>
                <div>
                    <input type="radio">
                    <label for="">5000</label>
                </div>
                <div>
                    <input type="radio">
                    <label for="">10000</label>
                </div>
                <div>
                    <input type="radio">
                    <label for="">15000</label>
                </div>
            </div>
            <NuxtLink to="/article-2/1">
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
                ease-in-out">submit</button>
            </NuxtLink>
        </div>
    </div>
</template>