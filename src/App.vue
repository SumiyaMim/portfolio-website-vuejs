<template>
    <div class="bg-[#D4EBF8] dark:bg-[#080326] min-h-screen">
        <Navbar/>
        <Hero/>
        <Counter/>
        <Services/>
    </div>
</template>

<script setup>
    import { defineAsyncComponent } from 'vue';

    //Import Components Asynchronously
    const Navbar = defineAsyncComponent(() => import('@/components/layout/Navbar.vue'));
    const Hero = defineAsyncComponent(() => import('@/components/layout/Hero.vue'));
    const Counter = defineAsyncComponent(() => import('@/components/layout/Counter.vue'));
    const Services = defineAsyncComponent(() => import('@/components/layout/Services.vue'));
</script>