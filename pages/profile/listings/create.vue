<script setup>
import CarAdSelect from '../../../components/CarAdSelect.vue';

definePageMeta({
    layout:"custom"
})
const {makes} = useCars()

const info=useState('adInfo',()=>{
    return {
        make:'',
        model:'',
        year:'',
        miles:'',
        price:'',
        city:'',
        seats:'',
        description:'',
        image:null,
    };
})
const onChangeInput=(data,name)=>{
    info.value[name]=data
}
</script>

<template>
    <div>
        <div>
            <h1 class="text-6xl mt-24">Create A New Listing</h1>
        </div>
        {{ info.make }}
        <div class="shadow rounded p-3 mt-5 flex flex-wrap justify-between">
            <CarAdSelect title="Make *" :options="makes" name="make" @changeInput="onChangeInput"/>
        </div>
    </div>
</template>

<!-- http://localhost:3000/profile/listings/create -->