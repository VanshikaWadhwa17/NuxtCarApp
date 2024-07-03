<script setup>
const route=useRoute()
useHead({
    title: `${route.params.make ? toTitleCase(route.params.make):"Cars"} in ${toTitleCase(route.params.city)}`,
});

function toTitleCase(str) {
  return str.replace(
    /\w\S*/g,
    text => text.charAt(0).toUpperCase() + text.substring(1).toLowerCase()
  );
}
definePageMeta({
  layout:"custom"
})
</script>
<template>
<div>
        <!-- cars page -->
        <div class="mt-32 flex">
          <CarSideBar/>
          <NuxtPage/>
        </div>
        <!-- cars page -->
    </div>
</template>