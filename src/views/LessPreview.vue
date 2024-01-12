<script setup>
import { ref } from 'vue';
import less from 'less';

const htmltext = ref(
  `
<div class="test">
  <h1>Get in touch!</h1>
  <p>Francesca McNulty</p>  
</div>
`
);
const lesstext = ref(
  `
.test {
  h1 {
    color: red;
  }
  p {
    color: blue;
  }
}
  `
);

const lessCompiled = () => {
  let cssOutput = '';
  less.render(lesstext.value, (error, output) => {
    if (error) {
      console.error(error);
    } else {
      cssOutput = output.css;
    }
  });
  return `<style>${cssOutput}</style>`;
};



</script>

<template>
  <main>
    <div class="grid">
      <div class="code">
        <label for="htmltext">HTML</label> &nbsp;
        <textarea id="htmltext" v-model="htmltext" rows="10">
        </textarea>
        <br />
        <label for="lesstext">Less</label> &nbsp;
        <textarea id="lesstext" v-model="lesstext" rows="10"></textarea>
      </div>
      <div class="preview">
        <div v-html="htmltext"></div>
        <div v-html="lessCompiled()"></div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 1rem;
  margin-bottom: 1rem;
}
</style>