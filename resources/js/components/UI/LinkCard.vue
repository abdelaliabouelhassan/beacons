<template>
<WaveButton class="hover:scale-[1.02]  rounded-full " :class="{'bouncing-button':bouncing}" @click="Redirect">
  <div class=" relative flex w-full h-[67.25px] py-2  px-4 text-[15px] bg-[#e9ecf0] text-2xl text-black font-poppins text-center">
     <div class=" absolute top-3 left-5">
      <slot></slot>
      </div>
    <div class="  flex m-auto items-center justify-center">
      <div class=" flex flex-col items-center -space-y-2">
        <span class=" capitalize">{{props.title}}</span>
        <span v-if="props.subtitle">{{props.subtitle}}</span>
      </div>
    </div>
  </div>
</WaveButton>

</template>

<script setup>
 const props = defineProps([
  'title',
  'subtitle',
  'icon',
  'bouncing',
  'url'
 ])
 import { onMounted } from "vue"
 import WaveButton from "./WaveButton.vue"
 const startBounceAnimation = () => {
    var button = document.querySelector('.bouncing-button');
    button.classList.add('bounce-animation');
  
    setTimeout(function() {
     button.classList.remove('bounce-animation');
     setTimeout(startBounceAnimation, 2000); // Repeat after 2 seconds
    }, 4000); // Duration of the bounce animation
 }
 const Redirect = () => {
  window.open(props.url, '_blank');
 }
 onMounted(() => {
   if(props.bouncing) startBounceAnimation();
 })
</script>


<style scoped>
@keyframes double-bounce {
  0%, 100% {
    transform: translateY(0);
  }
  30%, 70% {
    transform: translateY(-20px);
  }
  50% {
    transform: translateY(-10px);
  }
}

.bounce-animation {
  animation: double-bounce 1s linear;
}


</style>