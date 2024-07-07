<script setup>
const {cars}=useCars()

const favourite=useLocalStorage("favourite",{})
const handleFavourite=(id)=>{
    if(id in favourite.value){
        delete favourite.value[id]
    }
    else {
        favourite.value={...favourite.value,
        [id]:true
        }
    };
} 
//we want to call this handleFavourite fxn whenever in CarCard.vue the heart img is clicked so we need to emit an event from child  CarCard.vue to this parent CarCards.vue
</script>
<template>
    <div>
        <div class="w-full ">
            <ClientOnly>
            <CarCard v-for="car in cars" :key="car.id" :car="car" @favor="handleFavourite" :favored="car.id in favourite"/>
            </ClientOnly>
            <!-- here will have to listen to the emitted event favor from the child  and will also have to pass it as a prop to the child to get the proper heart image (filled/empty)-->
        </div>
    </div>
</template>