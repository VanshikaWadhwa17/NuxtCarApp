<template>
<div>
       <Navbar/>
        <!-- cars page -->
      <div class="mx-auto mt-4 max-w-7xl space-y-4 px-4 xs:px-8 sm:px-10 lg:px-16 pb-16 w-3/5">
        <div class="mt-32 flex">
          <CarSideBar/>
          <!-- car side bar -->
  
        <NuxtPage/>
        </div>
      </div>
        <!-- cars page -->
    </div>
</template>

<!-- here the NuxtPage will render any component thats inside the same route ie. this will render [[make]].vue -->