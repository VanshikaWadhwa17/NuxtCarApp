
import CarDetailHero from '../../components/CarDetailHero.vue';
<template>
    <div>
        <Navbar/>
        <!-- car detail page -->
      <div class="mx-auto mt-4 max-w-7xl space-y-4 px-4 xs:px-8 sm:px-10 lg:px-16 pb-16 w-3/5">
        
          <!-- car hero -->
          <CarDetailHero/>
          <!-- car hero -->

  <!-- removed extra enclosing divs here -->

          <!-- car attributes -->
          <CarDetailAttributes/>
          <!-- car attributes -->

          <!-- car description -->
          <CarDetailDescription/>
          <!-- car description -->
          <!-- car contact -->
          <CarDetailContact/>
          <!-- car contact -->
        </div>
        <!-- car detail page -->
    </div>
</template>