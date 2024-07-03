
import CarDetailHero from '../../components/CarDetailHero.vue';
<script setup>
const route= useRoute()
useHead({
    title: toTitleCase(route.params.name)
})
function toTitleCase(str) {
  return str.replace(
    /\w\S*/g,
    text => text.charAt(0).toUpperCase() + text.substring(1).toLowerCase()
  );
}
</script>
<template>
    <div>
        <!-- car detail page -->
      <div class="mx-auto mt-4 max-w-7xl space-y-4 px-4 xs:px-8 sm:px-10 lg:px-16 pb-16 w-3/5">
        
          <!-- car hero -->
          <CarDetailHero/>
          <!-- car hero -->

          <!-- car attributes -->
          <CarDetailAttributes/>
          <!-- car attributes -->

          <!-- car description -->
          <CarDetailDescription/>
          <!-- car description -->
          <!-- car contact -->
          <CarDetailContact/>
          <!-- car contact -->
        </div>
        <!-- car detail page -->
    </div>
</template>