<script setup>
import { ref } from 'vue';
import '@/config/db'; //En flad import
import { addDoc, collection, getFirestore } from 'firebase/firestore';

const db = getFirestore(); //Vi sætter en instans af vores firstore db

const shoeSize = ref(0);
const houseName = ref('');

const onSubmitForm = async () =>  {
  console.log("form submitted")
  const newHouse = await addDoc(collection(db, 'houses'), {
    houseName: houseName.value,
    shoeSize: shoeSize.value,
  })
};
</script>

<template>
<div>
  <form action="" @submit.prevent="onSubmitForm">
    <input type="text" v-model="houseName" placeholder="Enter House Name" />
    <input type="number" v-model="shoeSize" placeholder="Enter Shoe Size" />
   <button type="submit">submit</button>
  </form>
</div>
</template>

<style scoped>

</style>
