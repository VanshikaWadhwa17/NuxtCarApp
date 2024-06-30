<template>
  <!-- home hero -->
  <div class="relative h-screen w-full bg-no-repeat bg-cover bg-center" style="background-image: url('https://carconfigurator.ferrari.com/rt-assets/data/cars/sf90stradale/ui/splashpage.jpg');">
    <div class="z-10 absolute inset-0 flex justify-center items-center">
      <div class="text-center w-full px-4 sm:w-1/2">
        <h1 class="text-6xl sm:text-8xl font-serif mb-10 text-white">Find your drive</h1>
  
        <!-- home search bar -->
        <!-- <div class="font-serif w-[700px] text-2xl rounded-full bg-white flex justify-between overflow-hidden drop-shadow-2xl mx-auto">
          <input type="text" class="py-3 px-5 w-full text-2xl rounded-full focus:outline-none" placeholder="search by city..."/>
          <button class="bg-sky-500 px-10 text-white">Search</button>
        </div> -->

        <!-- home search bar -->
        <CarSearchBar />
  
      </div>
    </div>
    <!-- give a little dark tint  -->
    <div class="z-1 absolute w-full h-full bg-black opacity-50"></div>  
  </div>
  
      <!-- home hero -->
</template>