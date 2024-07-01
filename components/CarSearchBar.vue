<script setup>
import { navigateTo } from '#app';


const city=ref("")
const cityError=ref(false)

// const router=useRouter()
// const handleSearch=()=>{
//   router.push(`/city/${city.value}/car`)
// }

// Nuxt doesnt need to use this all it can simply do it with navigateTo() fxn:
const handleSearch=()=>{
  if(!city.value){
    return  cityError.value=true 
    //if city.value doesnt exist come out of the fxn - if this is not used it goes to /city//car- 404page
  }
  navigateTo(`/city/${city.value}/car`)
}
</script>
<template>
    <!-- home search bar -->
    <div class="font-serif w-[700px] text-2xl rounded-full bg-white flex justify-between overflow-hidden drop-shadow-2xl mx-auto">
          <input v-model="city" type="text" class="py-3 px-5 w-full text-2xl rounded-full focus:outline-none" placeholder="search by city..." :class="cityError ?'border-red-500 border':''">

          <button class="bg-sky-500 px-10 text-white" @click="handleSearch">Search</button>
        </div>
        <!-- home search bar -->
</template>