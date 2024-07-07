<script setup>
const {makes} =useCars()

const modal =ref({
  make: false,
  location: false,
  price: false
});
const city=ref("")
const priceRange=ref({
  min:'',
  max:''
})
const route = useRoute()
const router = useRouter()
// console.log(route.query)

const priceRangeText = computed(()=>{
  const minPrice=route.query.minPrice
  const maxPrice=route.query.maxPrice

  if(!minPrice && !maxPrice) return "Any"
  else if(!minPrice && maxPrice){
    return `<$${maxPrice}`
  }
  else if(minPrice && !maxPrice){
    return `>$${minPrice}`
  }
  else{
    return `$${minPrice}-$${maxPrice}`
  }
})

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
const onChangeMake=(make)=>{
  updateModal("make");
  navigateTo(`/city/${route.params.city}/car/${make}`)
}
const onChangePrice=(price)=>{
updateModal("price");
if(priceRange.value.max && priceRange.value.min){
  if(priceRange.value.min>priceRange.value.max) return 
  // essentially its better if we throw an error here but for now lets return early
router.push({
  query:{
    minPrice: priceRange.value.min,
    maxPrice: priceRange.value.max
  }
})
}

}
</script>
<template>
    <div>
        <!-- car side bar -->

        <!-- location start -->
        <div class="shadow border w-64 mr-10 z-30 h-[190px]">
            <div class="p-5 flex justify-between relative cursor-pointer border-b">
              <h3>Location</h3>
              <h3 @click="updateModal('location')" class="text-blue-400 captialize">{{route.params.city}}</h3>
              <div v-if="modal.location" class="absolute border shadow left-56 p-5 top-1 -m-1 bg-white">
                <input v-model="city" type="text" class="border p-1 rounded"/>
                <button @click="onChangeLocation" class="bg-blue-400 w-full mt-2 rounded text-white p-1">Apply</button> 
               </div>
            </div>
            <!-- location end -->

            <!-- make start -->
            <div class="p-5 flex justify-between relative cursor-pointer border-b">
              <h3>Make</h3>
              <h3 class="text-blue-400 captialize" @click="updateModal('make')">{{route.params.make || 'Any'}}</h3>
              <div class="absolute border shadow left-56 p-5 top-1 -m-1 w-[600px] flex justify-between flex-wrap bg-white z-50" v-if="modal.make">
                <h4 v-for="make in makes" :key="make" class="w-1/3" @click="onChangeMake(make)">{{ make }}</h4>
              </div>
            </div>
            <!-- make end -->

            <!-- price start -->
            <div class="p-5 flex justify-between relative cursor-pointer border-b">
              <h3>Price</h3>
              <h3 class="text-blue-400 captialize" @click="updateModal('price')">{{priceRangeText}}</h3>
              <div class="absolute border shadow left-56 p-5 top-1 -m-1 bg-white z-50" v-if="modal.price">
                <input class="border p-1 rounded" type="number" placeholder="Min" v-model="priceRange.min"/>
                <input class="border p-1 rounded" type="number" placeholder="Max" v-model="priceRange.max"/>
                <button class="bg-blue-400 w-full mt-2 rounded text-white" @click="onChangePrice">Apply</button>
              </div>
            </div>
            <!-- price end -->
  
          </div>
          <!-- car side bar -->
    </div>
</template>

<!-- NOTE: when we will add the min and max price- it will add a query parameter in the route itself like: 

http://localhost:3000/city/ottowa/car/Genesis?minPrice=4000&maxPrice=10000
-> if we manually put this URL in the tab- in the console.log(route.query)-> it will return an object in which we will have 2 values: minPrice =4000 and maxPrice=10000
if there is no query param: Any price range should be shown: for this we will use a computed property -->