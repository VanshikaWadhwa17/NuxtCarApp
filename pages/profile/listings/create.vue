<script setup>
import CarAdInput from '../../../components/CarAdInput.vue';
import CarAdSelect from '../../../components/CarAdSelect.vue';
import CarAdTextArea from '../../../components/CarAdTextArea.vue';

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
const inputs = [
  {
    id: 1,
    title: "Model *",
    name: "model",
    placeholder: "Civic",
  },
  {
    id: 2,
    title: "Year *",
    name: "year",
    placeholder: "2019",
  },
  {
    id: 3,
    title: "Miles *",
    name: "miles",
    placeholder: "10000",
  },
  {
    id: 4,
    title: "City *",
    name: "city",
    placeholder: "Austin",
  },
  {
    id: 5,
    title: "Number of Seats *",
    name: "seats",
    placeholder: "5",
  },
  {
    id: 6,
    title: "Features *",
    name: "features",
    placeholder: "Leather Interior, No Accidents",
  },
];
</script>

<template>
    <div>
        <div>
            <h1 class="text-6xl mt-24">Create A New Listing</h1>
        </div>
        <div class="shadow rounded p-3 mt-5 flex flex-wrap justify-between">
            <CarAdSelect title="Make *" :options="makes" name="make" @changeInput="onChangeInput"/>


            <CarAdInput v-for="input in inputs" :key="input.id" :title="input.title" :name="input.name" :placeholder="input.placeholder" @changeInput="onChangeInput"/>

            <CarAdTextArea title="Description" name="description" placeholder="" @changeInput="onChangeInput"/>

            <CarAdImage @changeInput="onChangeInput"/>
        </div>
    </div>
</template>

<!-- http://localhost:3000/profile/listings/create -->