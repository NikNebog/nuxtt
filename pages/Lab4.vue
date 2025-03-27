<template>
    <main class="flex flex-row gap-4 justify-center items-center h-screen bg-gradient-to-b from-gray-200 to-blue-300 hover:to-red-300 flex-wrap">
      <div class="flex gap-4">
        <label>
          <a :href="pic1.videoUrl" target="_blank" class="text-blue-500 hover:text-red-500">
            <input class="mx-2" type="radio" value="boris" v-model="selectedpic">Boris
          </a>
        </label>
        <label>
          <a :href="pic2.videoUrl" target="_blank" class="text-blue-500 hover:text-red-500">
            <input class="mx-2" type="radio" value="vitalya" v-model="selectedpic">Vitalya
          </a>
        </label>
        <label>
          <a :href="pic3.videoUrl" target="_blank" class="text-blue-500 hover:text-red-500">
            <input class="mx-2" type="radio" value="Sanyok" v-model="selectedpic">Sanyok
          </a>
        </label>
      </div>    
      
      <div class="flex flex-col gap-2 border-blue-500 border-1 bg-blue-300 w-72 h-auto items-center hover:border-red-500 border-2 hover:bg-red-300 rounded-xl">
        <img :src="pic1.image" class="w-60 h-68 pt-2">
        <p class="text-black text-xl">{{pic1.name}}</p>
      </div>
  
      <div class="flex flex-col gap-2 border-blue-500 border-1 bg-blue-300 w-72 h-auto items-center hover:border-red-500 border-2 hover:bg-red-300 rounded-xl">
        <img :src="pic2.image" class="w-60 h-68 pt-2">      
        <p class="text-black text-xl">{{ pic2.name }}</p>
      </div>
  
      <div class="flex flex-col gap-2 border-blue-500 border-1 bg-blue-300 w-72 h-auto items-center hover:border-red-500 border-2 hover:bg-red-300 rounded-xl">
        <img :src="pic3.image" class="w-60 h-68 pt-2">
        <p class="text-black text-xl">{{ pic3.name }}</p>
      </div>
      
      <div class="blockfor" v-for="(pic,index) in genpic" :key="index">
        <img :src="pic.image" class="w-60-h-68 pt-2">
        <p class="text-black text-xl">{{ pic.name }}</p>
      </div>      
    </main>
  </template>
  
  <script setup lang="ts">
  import { reactive, ref } from 'vue';
  
  interface stking {
    name: string;
    image: string;
    videoUrl: string;
  }
  
  const pic1 = reactive<stking>({
    name: 'Timur',
    image: "images/Tima.jpg",
    videoUrl: "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
  });
  
  const pic2 = reactive<stking>({
    name: 'Roman',
    image: "/images/Roma.jpg",
    videoUrl: "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
  });
  
  const pic3 = reactive<stking>({
    name: 'Nikitya',
    image: "/images/nik.jpg",
    videoUrl: "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
  });
  
  const genpic = reactive<stking[]>([
    { name: 'Elnur', image: "/images/Elnur.jpg", videoUrl: "https://www.youtube.com/watch?v=dQw4w9WgXcQ" },
    { name: 'Cat', image: "/images/Cat.jpg", videoUrl: "https://www.youtube.com/watch?v=dQw4w9WgXcQ" },
    { name: 'Skala', image: "/images/vitya.jpeg", videoUrl: "https://www.youtube.com/watch?v=dQw4w9WgXcQ" }
  ]);
  
  const selectedpic = ref<string>('');
  </script>
  
  <style scoped>
  .blockcap {
    @apply flex flex-col gap-2 border-blue-500 border bg-blue-300 w-72 h-auto items-center hover:border-red-500 hover:border-4 hover:bg-red-300 rounded-xl; 
  }
  
  .blockfor {
    @apply flex flex-col gap-2 border-blue-500 border bg-blue-300 w-72 h-auto items-center hover:border-yellow-500 hover:border-4 hover:bg-yellow-300 rounded-xl;
  }
  </style>