<template>
  <header class="flex flex-row w-full bg-green-400 border-b-2 border-gray-400 shadow-md shadow-gray-600 max-sm:justify-between max-sm:relative">
    <div class="basis-1/4 flex items-center justify-start px-4 min-w-40 max-sm:basis-auto">
      <img src="assets/images/LEGO.png" alt="Logo" class="w-16 h-16 p-2 bg-transparent">
    </div>
    <div class="basis-1/4 max-sm:basis-auto"></div>
    
    <nav class="hidden md:flex basis-3/4 flex-row items-center justify-end px-8 gap-4 ml-auto">
      <NuxtLink to="/" class="p-2 hover:bg-gray-500 hover:text-white rounded-md transition">Home</NuxtLink>
      
      <div class="relative group">
        <button @click="switch_submenu" class="p-2 border-b-2 border-black hover:text-white rounded-md transition">
          Labs
        </button>
        <div v-show="submenu" 
             class="absolute left-0 top-full w-40 bg-white shadow-lg border border-gray-300 rounded-md mt-2 
                    opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-300">
          <NuxtLink to="/lab3" class="block px-4 py-2 hover:bg-gray-500 hover:text-white transition">Lab3</NuxtLink>
          <NuxtLink to="/lab4" class="block px-4 py-2 hover:bg-gray-500 hover:text-white transition">Lab4</NuxtLink>
          <NuxtLink to="/lab5" class="block px-4 py-2 hover:bg-gray-500 hover:text-white transition">Lab5</NuxtLink>
          <NuxtLink to="/lab6" class="block px-4 py-2 hover:bg-gray-500 hover:text-white transition">Lab6</NuxtLink>
        </div>
      </div>
      <NuxtLink to="/login" class="p-2 hover:bg-gray-500 hover:text-white rounded-md transition">LogIn</NuxtLink>
      <NuxtLink to="/logout" class="p-2 hover:bg-gray-500 hover:text-white rounded-md transition">LogOut</NuxtLink>
    </nav>

    <div class="md:hidden flex items-center ml-auto">
      <button @click="switch_burger" class="p-2 bg-gray-700 text-white rounded-md">☰</button>
    </div>

    <nav v-if="burger" class="absolute top-full left-0 w-full bg-white flex flex-col items-center gap-2 p-4 shadow-lg md:hidden">
      <NuxtLink to="/" class="p-2 w-full text-center border-b">Home</NuxtLink>
      <button @click="switch_submenu" class="p-2 w-full text-center border-b">Labs</button>
      <div v-show="submenu" class="w-full bg-gray-100 rounded-md">
        <NuxtLink to="/lab3" class="block p-2 text-center border-b">Lab3</NuxtLink>
        <NuxtLink to="/lab4" class="block p-2 text-center border-b">Lab4</NuxtLink>
        <NuxtLink to="/lab5" class="block p-2 text-center border-b">Lab5</NuxtLink>
        <NuxtLink to="/lab6" class="block p-2 text-center border-b">Lab6</NuxtLink>
      </div>
      <NuxtLink to="/login" class="p-2 w-full text-center border-b">Login</NuxtLink>
      <NuxtLink to="/logout" class="p-2 w-full text-center border-b">Logout</NuxtLink>
    </nav>
  </header>


  <main class="p-5 flex bg-green-100 h-screen">
    <slot />
  </main>

  <footer class="flex flex-row w-full bg-green-400 border-2 border-gray-400 items-center justify-center px-4 py-2 gap-4">
        <a href="https://www.youtube.com/"><img src="/assets/images/yout.png" class="w-16 h-16"></a>
        <a href="https://github.com/"><img src="/assets/images/git.png" class="w-16 h-16"></a>
        <a href="https://www.facebook.com/"><img src="/assets/images/fb.png" class="w-16 h-16 bg-transparent"></a>
  </footer>
</template>





<script setup>
import { useHead } from '#app';
import { ref } from 'vue';


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
            
            src: "https://www.googletagmanager.com/gtag/js?id=G-8V5TJWBREN",
        },
        {
            innerHTML: `
                window.dataLayer = window.dataLayer || [];
                function gtag(){dataLayer.push(arguments);}
                gtag('js', new Date());

                gtag('config', 'G-8V5TJWBREN');
                `,
            type: 'text/javascript',
        },
    ],
        _dangerouslyDisableSanitizerByTagID: {
            dtag: ['innerHTML'],
        },
});


</script>