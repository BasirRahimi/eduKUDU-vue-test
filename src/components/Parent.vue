<script setup>
import { ref } from 'vue';
import Child from './Child.vue';

const theObject = ref({ theBoolean: true, theString: '' });
const updateTheObject = (data) => {
  theObject.value = data.theObject;
}
</script>

<template>
  <div>
    <p>The Boolean value is: {{ theObject.theBoolean }}</p>
    <p>The String value is: {{ theObject.theString }}</p>
    <br />
    <br />
    <Child :theObject="theObject" @update="updateTheObject" />
  </div>
</template>
