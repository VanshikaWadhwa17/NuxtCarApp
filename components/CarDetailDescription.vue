<script setup>
const props=defineProps({
  description:String,
})
</script>
<template>
    <div>
        <div class="mt-5">
            <p class="mb-10">
              {{description}}
            </p>
          </div>
    </div>
</template>