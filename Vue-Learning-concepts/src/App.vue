<!-- This is to practice Composition API -->
<script setup>
import { ref, onMounted } from 'vue';
    const name = ref('John Doe');
    const selected = ref('Pending');
    const tasks = ref([1,2,3,4]);
    const light = ref('ON');
    const link = ref('https://google.com');
    const newTask = ref('')
    const switchLight = () => {
        console.log('Hiii')
      light.value  = (light.value === "ON") ? 'OFF':"ON" 
    }

    const addTask = () =>{
      console.log('hiiiii');
if(newTask.value.trim() !== ''){
  tasks.value.push(newTask.value);
}
    }

    const delTask = (index) => {
tasks.value.splice(index,1)
    }

    onMounted(async()=>{
        try{

          const resp = await fetch('https://jsonplaceholder.typicode.com/todos');
          const data = await resp.json();
          tasks.value = data.map((datum)=>datum.title)

        } catch (error) {
          console.log('Error');
        }
    })
  
</script>



<template>

<!-- <form v-on:submit.prevent="addTask"> -->
  <form @submit.prevent="addTask">

  <label for="newtask"> Add New Task</label>
  <input id="newtask" name="newtask" v-model="newTask" />
  <button type="submit">Add Task</button>
</form>

  <h1>This is the Job Application</h1>
  <br>
  <h2>Hi {{ name }}</h2>
  <p v-if="selected==='Yes'">You are hired</p>
  <p v-else-if="selected==='Pending'">You status is pending</p>
  <p v-else>You are not hired</p>

  <br>
  <h3>
    <ul>
      <li v-for="(task,index) in tasks" :key="task">
        <span> {{ task }}</span>
        <button @click="delTask(index)">Delete</button>
       </li>
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