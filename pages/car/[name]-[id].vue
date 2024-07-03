
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
definePageMeta({
  layout:"custom"
})
</script>
<template>
    <div>
        <!-- car detail page -->
          <CarDetailHero/>
          <CarDetailAttributes/>
          <CarDetailDescription/>
          <CarDetailContact/>
        <!-- car detail page -->
    </div>
</template>