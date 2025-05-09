<template>
    <div class="bg-[#D4EBF8] dark:bg-[#080326] min-h-screen">
        <Navbar/>
        <Hero/>
    </div>
</template>

<script setup>
    import { defineAsyncComponent } from 'vue';

    //Import Components Asynchronously
    const Navbar = defineAsyncComponent(() => import('@/components/layout/Navbar.vue'));
    const Hero = defineAsyncComponent(() => import('@/components/layout/Hero.vue'));
</script>