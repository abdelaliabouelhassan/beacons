<template>
    <button @click="Open" class=" rounded-full w-8 h-8 z-10 bg-gray-100 flex items-center justify-center hover:bg-gray-100 hover:opacity-70 css-1j7qk7u">
                    <svg class="h-5 w-5 text-gray-700 fill-current " focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="ShareIcon" alt="share dialog icon"><path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"></path></svg>
    </button>
    <div v-if="show" class="relative z-20" aria-labelledby="modal-title" role="dialog" aria-modal="true">
   
    <div class="fixed inset-0 bg-black bg-opacity-50 transition-opacity"></div>

    <div class="fixed inset-0 z-20 overflow-y-auto">
        <div class="flex min-h-full justify-center p-4 text-center items-center sm:p-0">

            <div class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 w-full max-w-lg">
               <button @click="Close" class=" p-1 bg-opacity-50 absolute top-2 right-2 rounded-full hover:bg-gray-200">
                <svg  class=" w-6 h-6" focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="CloseIcon"><path d="M19 6.41 17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"></path></svg>
               </button>

               <div class="  flex justify-center flex-col items-center space-y-2 pt-4 pb-5">
                 <img class=" w-12 h-12 rounded-full" src="https://cdn.beacons.ai/user_content/HlbMPOT3eBYbFLSItMO6W4r3xtn1/profile_sereda.png?t=1658457397570" alt="">
                <span class=" uppercase font-bold truncate">SHARE @SEREDA'S BEACONS</span> 
               </div>

               <div class=" w-full space-y-2 p-2">
                <button @click="copy" class=" w-full p-2 flex justify-between items-center border rounded-md cursor-pointer hover:bg-gray-200 no-underline font-bold    py-3  border-gray-200 border-solid rounded-8">
                    <div class=" flex items-center space-x-2">
                        <img alt="Beacons share dialog icon" class="rounded-md h-7 w-7 mx-0.5 my-0 border border-gray-100 border-solid" src="https://cdn.beacons.ai/images/platform_icons/beacons.png">
                        <span class=" truncate">beacons.ai/sereda</span>
                    </div>
                    <div>
                        <svg class=" h-6 w-6 text-black fill-current text-opacity-25" focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="FileCopyIcon"><path d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm-1 4 6 6v10c0 1.1-.9 2-2 2H7.99C6.89 23 6 22.1 6 21l.01-14c0-1.1.89-2 1.99-2h7zm-1 7h5.5L14 6.5V12z"></path></svg>
                    </div>
                </button>
                <div class=" w-full border"></div>
                <a target="_blank" :href="item.link" v-for="(item,index,key) in links" :key="key" @click="copy" class=" w-full p-2 flex justify-between items-center border rounded-md cursor-pointer hover:bg-gray-200 no-underline font-bold    py-3  border-gray-200 border-solid rounded-8">
                    <div class=" flex items-center space-x-2">
                        <img alt="Beacons share dialog icon" class="rounded-md mx-0.5 my-0 h-7 w-7 border border-gray-100 border-solid" :src="item.img">
                        <span class=" truncate">{{ item.title}}</span>
                    </div>
                    <div>
                        <svg class=" h-6 w-6 text-black fill-current text-opacity-25" focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="LaunchIcon"><path d="M19 19H5V5h7V3H5c-1.11 0-2 .9-2 2v14c0 1.1.89 2 2 2h14c1.1 0 2-.9 2-2v-7h-2v7zM14 3v2h3.59l-9.83 9.83 1.41 1.41L19 6.41V10h2V3h-7z"></path></svg>
                    </div>
                </a>
                <a  :href="'mailto:?subject= Check out this Beacons page! &body= Check out this Beacons page! - ' + url" class=" w-full p-2 flex justify-between items-center border rounded-md cursor-pointer hover:bg-gray-200 no-underline font-bold    py-3  border-gray-200 border-solid rounded-8">
                    <div class=" flex items-center space-x-2">
                        <svg class=" h-6 w-6 border border-gray-100 border-solid " focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="EmailIcon"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4-8 5-8-5V6l8 5 8-5v2z"></path></svg>
                        <span class=" truncate">Share via Email</span>
                    </div>
                    <div>
                        <svg class=" h-6 w-6 text-black fill-current text-opacity-25" focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="LaunchIcon"><path d="M19 19H5V5h7V3H5c-1.11 0-2 .9-2 2v14c0 1.1.89 2 2 2h14c1.1 0 2-.9 2-2v-7h-2v7zM14 3v2h3.59l-9.83 9.83 1.41 1.41L19 6.41V10h2V3h-7z"></path></svg>
                    </div>
                </a>
               </div>
              <div class=" flex justify-end px-4 py-4">
                <WaveButton @click="Close" class=" bg-[#1c1c1c] max-w-[70px] rounded-md p-2">
                    <span class=" text-white font-bold">Close</span>
                </WaveButton>
              </div>
            </div>
        </div>
    </div>
    </div>

   <div v-if="copied" class=" w-full fixed z-50 bottom-3 left-0  flex" style="opacity: 1; transform: none; transition: opacity 225ms cubic-bezier(0.4, 0, 0.2, 1) 0ms, transform 150ms cubic-bezier(0.4, 0, 0.2, 1) 0ms;">
     <div class=" max-w-[180px] w-full p-2 mx-auto   z-50 bg-[#14A111] rounded-md text-white flex items-center justify-between">
        <svg class=" w-6 h-6 fill-current text-white" focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="SuccessOutlinedIcon"><path d="M20,12A8,8 0 0,1 12,20A8,8 0 0,1 4,12A8,8 0 0,1 12,4C12.76,4 13.5,4.11 14.2, 4.31L15.77,2.74C14.61,2.26 13.34,2 12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0, 0 22,12M7.91,10.08L6.5,11.5L11,16L21,6L19.59,4.58L11,13.17L7.91,10.08Z"></path></svg>
        <span>Link copied!</span>
        <button @click="copied = false" class=" bg-opacity-80 rounded-full p-1">
                <svg  class=" text-white w-6 h-6 fill-current" focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="CloseIcon"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"></path></svg>
        </button>
    </div>
   </div>

</template>


<script setup>
    import WaveButton from "./WaveButton.vue"
    import { onMounted, onUnmounted, ref } from "vue";
    const show = ref(false);
    const  copied = ref(false)
    const url = window.location.href;
    const links = ref([
        {
            title:'Share on Facebook',
            img:'https://cdn.beacons.ai/images/platform_icons/facebook.png',
            link:'https://www.facebook.com/sharer.php?u=' + url,
        },
         {
            title:'Share on LinkedIn',
            img:'https://cdn.beacons.ai/images/platform_icons/linkedin.png',
            link:'https://www.linkedin.com/sharing/share-offsite/?url=' + url,
        },
         {
            title:'Share on Twitter',
            img:'https://cdn.beacons.ai/images/platform_icons/twitter.png',
            link:'https://twitter.com/intent/tweet?text=Check%20out%20this%20Beacons%20page!%20-%20'+ url,
        },
         {
            title:'Share via WhatsApp',
            img:'https://cdn.beacons.ai/images/platform_icons/whatsapp.png',
            link:'https://wa.me/?text=Check%20out%20this%20Beacons%20page!%20-%20'+ url,
        },
         {
            title:'Share via Messenger',
            img:'https://cdn.beacons.ai/images/platform_icons/messenger.png',
            link:'https://www.messenger.com/new',
        },
        
        

    ])
    const copy = () => {
        const url = window.location.href;
        navigator.clipboard.writeText(url);
        copied.value = true;
        setTimeout(() => {
            copied.value = false;
        }, 2000);
    }

    const Close = () => {
        show.value = false;
        document.body.classList.remove('overflow-hidden');
    }

    const Open = () => {
         show.value = true;
         document.body.classList.add('overflow-hidden');
    }
</script>