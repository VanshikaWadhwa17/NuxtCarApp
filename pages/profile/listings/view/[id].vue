
import CarMessageCard from '../../../../components/CarMessageCard.vue';
<script setup>
definePageMeta({
    layout:"custom"
})
</script>
<template>
    <div class="rounded shadow mt-20">
        <div>
            <CarMessageCard/>
            <CarMessageCard/>
            <CarMessageCard/>
            <CarMessageCard/>
        </div>
    </div>
</template>