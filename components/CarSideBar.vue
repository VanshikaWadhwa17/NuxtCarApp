<script setup>
const modal =ref({
  make: false,
  location: false,
  price: false
});
const city=ref("")
const route = useRoute()

const updateModal=(key)=>{
  modal.value[key]= !modal.value[key]
}
const onChangeLocation=()=>{
  // updateModal("location")
  if(!city.value) return
  if(!isNaN(parseInt(city.value))){
    throw createError({
      statusCode: 400,
      message: "Invalid City Format"
    }) // this is a client side error- it will not take us to an error.vue instead it will throw a client side error in the console
  }
  updateModal("location")
  navigateTo(`/city/${city.value}/car/${route.params.make}`)
}
</script>
<template>
    <div>
        <!-- car side bar -->
        <div class="shadow border w-64 mr-10 z-30 h-[190px]">
            <div class="p-5 flex justify-between relative cursor-pointer border-b">
              <h3>Location</h3>
              <h3 @click="updateModal('location')" class="text-blue-400 captialize">{{route.params.city}}</h3>
              <div v-if="modal.location" class="absolute border shadow left-56 p-5 top-1 -m-1 bg-white">
                <input v-model="city" type="text" class="border p-1 rounded"/>
                <button @click="onChangeLocation" class="bg-blue-400 w-full mt-2 rounded text-white p-1">Apply</button> 
               </div>
            </div>
            <div class="p-5 flex justify-between relative cursor-pointer border-b">
              <h3>Make</h3>
              <h3 class="text-blue-400 captialize">Toyota</h3>
            </div>
            <div class="p-5 flex justify-between relative cursor-pointer border-b">
              <h3>Price</h3>
              <h3 class="text-blue-400 captialize">Any</h3>
            </div>
  
          </div>
          <!-- car side bar -->
    </div>
</template>