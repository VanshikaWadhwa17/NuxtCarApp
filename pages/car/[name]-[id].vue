
import CarDetailHero from '../../components/CarDetailHero.vue';
<script setup>
const route= useRoute()
const {cars}= useCars()
const {toTitleCase}=useUtilities()
useHead({
    title: toTitleCase(route.params.name)
});

const car=computed(()=>{
return cars.find((c)=>{
  return c.id===parseInt(route.params.id)
})
})
definePageMeta({
  layout:"custom"
})
if(!car.value){
  throw createError({
    statusCode:404,
    message:`Car with ID of ${route.params.id} does not exist `
  })
}
</script>
<template>
    <div>
        <!-- car detail page -->
          <CarDetailHero :car="car"/>
          <CarDetailAttributes :features="car.features"/>
          <CarDetailDescription :description="car.description"/>
          <CarDetailContact/>
        <!-- car detail page -->
    </div>
</template>