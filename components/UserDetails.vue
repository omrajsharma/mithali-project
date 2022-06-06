<template>
<div class="w-screen h-screen flex items-center justify-center">

    <div class="m-4">
        <div class="block p-6 rounded-lg shadow-lg bg-white max-w-md">
            <div class="mb-4">
                <span class="text-lg">
                    Registration
                </span>
                <hr>
            </div>
            <form>
                <div class="grid grid-cols-2 gap-4">
                <div class="form-group mb-6">
                    <input type="text" class="form-control
                    block
                    w-full
                    px-3
                    py-1.5
                    text-base
                    font-normal
                    text-gray-700
                    bg-white bg-clip-padding
                    border border-solid border-gray-300
                    rounded
                    transition
                    ease-in-out
                    m-0
                    focus:text-gray-700 focus:bg-white focus:border-cyan-600 focus:outline-none" id="exampleInput123"
                    aria-describedby="emailHelp123" placeholder="Full name" required>
                </div>
                <div class="form-group mb-6">
                    <input type="number" class="form-control
                    block
                    w-full
                    px-3
                    py-1.5
                    text-base
                    font-normal
                    text-gray-700
                    bg-white bg-clip-padding
                    border border-solid border-gray-300
                    rounded
                    transition
                    ease-in-out
                    m-0
                    focus:text-gray-700 focus:bg-white focus:border-cyan-600 focus:outline-none" id="exampleInput124"
                    aria-describedby="emailHelp124" placeholder="Mobile Number" required>
                </div>
                </div>
                <div class="form-group mb-6">
                <input type="email" class="form-control block
                    w-full
                    px-3
                    py-1.5
                    text-base
                    font-normal
                    text-gray-700
                    bg-white bg-clip-padding
                    border border-solid border-gray-300
                    rounded
                    transition
                    ease-in-out
                    m-0
                    focus:text-gray-700 focus:bg-white focus:border-cyan-600 focus:outline-none" id="exampleInput125"
                    placeholder="Email" required>
                </div>
                <div class="form-group mb-6">
                    <select class="form-select appearance-none
                    block
                    w-full
                    px-3
                    py-1.5
                    text-base
                    font-normal
                    text-gray-700
                    bg-white bg-clip-padding bg-no-repeat
                    border border-solid border-gray-300
                    rounded
                    transition
                    ease-in-out
                    m-0
                    focus:text-gray-700 focus:bg-white focus:border-cyan-600 focus:outline-none" aria-label="Gender" required>
                        <option selected disabled>Gender</option>
                        <option value="male">Male</option>
                        <option value="female">Female</option>
                        <option value="others">Others</option>
                    </select>
                </div>
                <button @click="login" type="submit" class="
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
            </form>
        </div>
    </div>
</div>
</template>


<script>
export default {
    props: ['user', 'login'],
}
</script>
