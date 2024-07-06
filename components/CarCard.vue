<script setup>
import heartFilled from "@/assets/heartFilled.png"
import heartOutline from "@/assets/heartOutline.png"

const  props = defineProps({
  car:Object,
});

// useState - to store and manipulate state - better than using refs as its more server side friendly

// const favored=useState('favored',()=>{
//   return false
// }) 
// this is using a key which is same for all the cars hence when we click on one empty heart it will fill all hearts - to rectify we need to give a unique key by attaching car id to it:

const favored=useState(`favored-${props.car.id}`,()=>{
  return false
}) 

</script>
<template>
    <div>
        <!-- single car card -->
        <div class="relative shadow border w-full overflow-hidden mb-5 cursor-pointer h-[200px]"> 
          <img @click="favored=!favored" class="absolute w-7 right-5 top-2 z-20" :src="favored?heartFilled:heartOutline" alt=""/>
              <div class="flex h-full w-[700px]" @click="navigateTo(`/car/${car.name}-${car.id}`)">
                <NuxtImg :src="car.url" alt=""
                class="w-[300px] h-full"/>
                <div class="p-4 flex flex-col">
                  <h1 class="text-2xl text-blue-700">{{ car.name }}</h1>
                  <p class="text-gray-700">{{ car.description }}</p>
                  <h1 class="mt-auto text-xl">${{car.price}}</h1>
                </div>
              </div>
            </div>
            <!-- single car card -->
    </div>
</template>