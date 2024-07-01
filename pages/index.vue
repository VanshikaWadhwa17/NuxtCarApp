<!-- <script setup>
import Navbar from "../components/Navbar.vue"
</script> -->


<!-- in Nuxt we dont need this explicit import, Nuxt auto imports from the components directory  -->


<!-- if components are directly placed in the components directory, auto import is done by nuxt but if those components are deeply nested like Hero is placed at /components/Car/Hero.vue then we need to explicitly import it as done above -->

<template>
    <div>
       <Navbar/>
       <CarHero/>
    </div> 
</template>
  