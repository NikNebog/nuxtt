<template>
    <header class="flex flex-row w-full items-center relative bg-green-400 border-2 border-gray-400 px-4">
        <div class="basis-1/4 flex items-center justify-start px-8 min-w-max">
            <img src="/assets/images/images.jpeg" class="w-16 h-16 bg-transparent">
        </div>

        <nav class="hidden md:flex basis-3/4 flex-row items-center justify-end px-8 gap-4 ml-auto">
            <NuxtLink to="/" class="p-2 hover:bg-gray-500 hover:text-white">Home</NuxtLink>

            <div class="relative">
                <button @click="switch_submenu" class="p-2 border-b-2 border-black hover:text-white">
                    Labs
                </button>
                <div v-show="submenu" class="absolute left-0 top-full w-32 bg-white shadow-lg border border-gray-300">
                    <NuxtLink to="/Lab3" class="block p-2 hover:bg-gray-500 hover:text-white">Lab3</NuxtLink>
                    <NuxtLink to="/Lab4" class="block p-2 hover:bg-gray-500 hover:text-white">Lab4</NuxtLink>
                    <NuxtLink to="/Lab5" class="block p-2 hover:bg-gray-500 hover:text-white">Lab5</NuxtLink>
                    <NuxtLink to="/Lab6" class="block p-2 hover:bg-gray-500 hover:text-white">Lab6</NuxtLink>
                </div>
            </div>

            <NuxtLink to="/Login" class="p-2 hover:bg-gray-500 hover:text-white">Login</NuxtLink>
            <NuxtLink to="/Logout" class="p-2 hover:bg-gray-500 hover:text-white">Logout</NuxtLink>
        </nav>

        <div class="md:hidden flex items-center ml-auto">
            <button @click="switch_burger" class="p-2 bg-gray-700 text-white rounded-md">
                ☰
            </button>
        </div>

        <nav v-if="burger" class="absolute top-full left-0 w-full bg-white flex flex-col items-center gap-2 p-4 shadow-lg md:hidden">
            <NuxtLink to="/" class="p-2 w-full text-center border-b">Home</NuxtLink>
            <NuxtLink to="/Lab3" class="p-2 w-full text-center border-b" @click="switch_submenu">Labs</NuxtLink>

            <div v-show="submenu" class="w-full bg-gray-100">
                <NuxtLink to="/Lab3" class="block p-2 text-center border-b">Lab3</NuxtLink>
                <NuxtLink to="/Lab4" class="block p-2 text-center border-b">Lab4</NuxtLink>
                <NuxtLink to="/Lab5" class="block p-2 text-center border-b">Lab5</NuxtLink>
                <NuxtLink to="/Lab6" class="block p-2 text-center border-b">Lab6</NuxtLink>
            </div>

            <NuxtLink to="/Login" class="p-2 w-full text-center border-b">Login</NuxtLink>
            <NuxtLink to="/Logout" class="p-2 w-full text-center border-b">Logout</NuxtLink>
        </nav>
    </header>

    <main class="p-5 flex bg-green-100 h-screen">
        <slot />
    </main>

    <footer class="flex flex-row w-full bg-green-400 border-2 border-gray-400 items-center justify-center px-4 py-2 gap-4">
        <a href="https://www.youtube.com/"><img src="/assets/images/youtube.jpg" class="w-16 h-16"></a>
        <a href="https://github.com/"><img src="/assets/images/github.png" class="w-16 h-16"></a>
        <a href="https://www.facebook.com/"><img src="/assets/images/facebook.png" class="w-16 h-16 bg-transparent"></a>
    </footer>
</template>

<script setup>
import { ref } from 'vue';
import { useHead } from '#app';

const submenu = ref(false);
const burger = ref(false);

const switch_submenu = () => {
    submenu.value = !submenu.value;
};

const switch_burger = () => {
    burger.value = !burger.value;
};

useHead({
    script: [
        {
            async: true,
            src: "https://www.googletagmanager.com/gtag/js?id=G-L5ZC73SL45",
        },
        {
            innerHTML: `
                window.dataLayer = window.dataLayer || [];
                function gtag(){dataLayer.push(arguments);}
                gtag('js', new Date());
                gtag('config', 'G-L5ZC73SL45');
            `,
            type: 'text/javascript',
        },
    ],
    _dangerouslyDisableSanitizerByTagID: {
        dtag: ['innerHTML'],
    },
});
</script>
