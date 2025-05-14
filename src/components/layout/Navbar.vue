<template>
    <header>
        <div class='flex justify-between items-center px-8 lg:px-12 py-8 relative z-20'>
            <div class="dark:text-white text-primary text-2xl lg:text-3xl font-bold">LOGO</div>
        
            <!-- Mobile Toggle Button -->
            <div class="md:hidden z-30">
                <button class="block focus:outline-none" @click="isMenuOpen = !isMenuOpen">
                    <span v-if="isMenuOpen" class="text-4xl lg:text-5xl md:text-primary text-white dark:text-white">
                        <Icon icon="material-symbols:close"/>
                    </span>
                    <span v-else class="text-4xl lg:text-5xl md:text-primary dark:text-white text-primary">
                        <Icon icon="material-symbols:menu"/>
                    </span>
                </button>
            </div>

            <!-- Navbar Link -->
            <nav
            :class="['fixed inset-0 z-20 flex flex-col items-center justify-center bg-[#111827] md:relative md:bg-transparent md:flex md:justify-between md:flex-row',
                isMenuOpen ? 'block':'hidden'
            ]"
            >
                <ul class="flex flex-col items-center space-y-5 md:flex-row md:space-x-6 md:space-y-0">
                    <li v-for="item in Menu" :key="item.name">
                        <a :href="item.href" 
                        class="block transition ease-linear text-lg md:text-base lg:text-lg font-bold text-white dark:md:text-white md:text-primary dark:hover:text-secondary"
                        @click="scrollToSection(item.href)"
                        >
                            {{ item.name }}
                        </a>
                    </li>
                </ul>
                <button @click="toggleDarkMode" class="text-white ml-10 z-10 hidden md:block">
                    <!-- Show moon icon if dark mode is off, otherwise show sun icon -->
                    <Icon v-if="!isDarkMode" icon="line-md:moon-filled" class="text-4xl text-primary"/>
                    <Icon v-else icon="line-md:sunny-outline" class="text-4xl text-secondary"/>
                </button>
            </nav>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue';
const isMenuOpen =ref(false)
const Menu =ref([
    {name:'Home',href:'#home'},
    {name:'About',href:'#whyme'},
    {name:'Services',href:'#services'},
    {name:'Skills',href:'#skills'},
    {name:'Projects',href:'#projects'},
    {name:'Contact',href:'#contact'},
]);

const scrollToSection =(href)=>{
    isMenuOpen.value=false;
    const section=document.querySelector(href);
    if(section){
        section.scrollIntoView({behavior :'smooth'});
    }
}

// Reactive property to track dark mode state
const isDarkMode = ref(localStorage.getItem('theme') === 'dark')

const toggleDarkMode = () => {
    const html = document.documentElement;
    if(isDarkMode.value){
        html.classList.remove('dark');
        localStorage.setItem('theme', 'light')
    }
    else{
        html.classList.add('dark');
        localStorage.setItem('theme', 'dark')
    }

    // Update dark mode state
    isDarkMode.value = !isDarkMode.value;
}
</script>
