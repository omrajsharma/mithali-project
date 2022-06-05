<template>
    <div class="w-screen h-screen flex items-center justify-center bg-cyan-500">
        <div class="block p-6 rounded-lg shadow-lg bg-white w-screen max-w-md">
            <div align="center" class="text-3xl font-medium">
                Thank You 🙏
            </div>
            <div class="mt-6">
                <NuxtLink to="/">
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
                ease-in-out">Go to home</button>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>