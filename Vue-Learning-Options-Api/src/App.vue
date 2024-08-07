<script >
export default {
  data() {
    return {
      name:'John Doe',
      selected:'Pending',
      tasks: [1,2,3,4],
      light : 'ON',
      link:"https://google.com"
    }
  },
  methods:{
    switchLight() {
      console.log('Hiii')
      this.light  = (this.light === "ON") ? 'OFF':"ON"
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