<template>
     <div class=" w-full bg-[#e9ecf0] rounded-3xl px-5 py-10 flex flex-col items-center space-y-5">
                <div class=" flex flex-col items-center space-y-2">
                    <span class=" font-bold text-lg font-poppins text-black">Stay Updated</span>
                    <span class=" text-black font-poppins font-semibold">Sign up to get all the new drops</span>
                </div>
                <div class=" w-full space-y-5">
                    <input type="text" placeholder="Full Name" class=" w-full outline-none rounded-full h-14  ring-[2.5px] text-lg ring-black px-4 bg-transparent">
                    <input type="email" placeholder="Email" class=" w-full outline-none rounded-full h-14 ring-[2.5px] text-lg ring-black px-4 bg-transparent">
                </div>
                <WaveButton class=" bg-black py-5 hover:scale-[1.02] rounded-full">
                    <span class=" text-white font-poppins text-center font-medium">Join</span>
                </WaveButton>
         </div>
</template>


<script setup>
 import WaveButton from "./WaveButton.vue"
</script>