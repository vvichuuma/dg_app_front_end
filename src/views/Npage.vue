<template>
  <div class="home">
    <h1>{{ message }}</h1>
    
   <input v-model="message" placeholder="Edit_me">
    <button v-on:click="simple()">Submit</button>
    <h1>UserOverview</h1>
    <p>TeamId:{{ $route.params.id }}</p>
  
  </div>
</template>

<style>
</style>

<script>
export default {
  data: function() {
    return {

      message: "Vishnu is a Fucking Computer Programmer"
    };
  },
  created: function() {
 

 


  },
  methods: {



  },
  computed: {}
};
</script>