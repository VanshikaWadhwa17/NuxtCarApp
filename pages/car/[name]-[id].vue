
import CarDetailHero from '../../components/CarDetailHero.vue';
<script setup>
const route= useRoute()
const {toTitleCase}=useUtilities()
useHead({
    title: toTitleCase(route.params.name)
})

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