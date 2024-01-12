
<script setup>
import { ref, defineEmits } from 'vue';

const props = defineProps({
  theObject: Object,
});

const emit = defineEmits(['update']);

const theString = ref(props.theObject.theString);
const theBoolean = ref(props.theObject.theBoolean);

const updateTheString = (e) => {
  // Could use v-model on the input instead but this flow looks nicer.
  // theString.value = e.target.value;
  emit('update', { theObject: { theString: theString.value, theBoolean: theBoolean.value } });
};

const updateBoolean = () => {
  theBoolean.value = !theBoolean.value;
  emit('update', { theObject: { theString: theString.value, theBoolean: theBoolean.value } });
}
</script>

<template>
  <div>
    <button @click="updateBoolean">Change bool</button>
    <br />
    <input type="text" @input="updateTheString" v-model="theString" />
  </div>
</template>