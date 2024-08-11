<!-- This is to practice Composition API -->
<script >
import { ref } from 'vue';
export default {
  setup() {
    const name = ref('John Doe');
    const selected = ref('Pending');
    const tasks = ref([1,2,3,4]);
    const light = ref('ON');
    const link = ref('https://google.com');
    
    const switchLight = () =>{
        console.log('Hiii')
      light.value  = (light.value === "ON") ? 'OFF':"ON" 
    }


    return {
      name,
      selected,
      tasks,
      light,
      link,
      switchLight
    }
  }
}
</script>

<template>
  <h1>This is the Job Application</h1>
  <br>
  <h2>Hi {{ name }}</h2>
  <p v-if="selected==='Yes'">You are hired</p>
  <p v-else-if="selected==='Pending'">You status is pending</p>
  <p v-else>You are not hired</p>

  <br>
  <h3>
    <ul>
      <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
  </h3>

  <br>
<h3><a :href="link">{{ link }}</a></h3>
<h3><a v-bind:href="link">click for google</a></h3>
<a href="https://google.com">click for google</a>

<br>
<br>
<p> The light is {{ light }}</p>
<button v-on:click="switchLight">Switch</button>
<button @click="switchLight">Switch</button>

</template>

<style scoped>
h1{
color:blue;
}
</style>