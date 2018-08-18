
<template>
  <div class="home">
  
    <ol>
    <li v-for="survey in surveyItems">
      <h6>{{survey.question}}</h6>
       <span v-for="choice in choices">
         <input  type="radio" v-on:click="click(choice,survey.graph)" v-bind:value="choice" v-model="survey.answer"  >
         <label>{{ choice }} &emsp; </label> 
       </span>
    </li>
  </ol>


  <button v-on:click="result()">Calculate</button>

  </div>
</template>

<style>
</style>

<script>
var axios = require("axios");
console.log(axios);

export default {
  data: function() {
    return {
      message: "Vishnu is an american Computer Programmer",
      choices: [],
      compares: [],
      persons: [],
      ans: [],
      surveyItems: [
        { question: "Who is the most intelligent?", answer: "",graph: "intelligence" },
        { question: "Who's the most smart?", answer: "",graph: "smart" },
        {
          question: "Who is the most Handsome Person in the group?",
          answer: "",graph: "handsome"
        }
      ]
    };
  },
  created: function() {
    axios.get("http://localhost:3000/api/inde").then(
      function(response) {
        console.table(response.data);
        var ar = response.data;
        ar.forEach(
          function(arr) {
            this.choices.push(arr.name);
          }.bind(this)
        );
      }.bind(this)
    );
  },
  methods: {

    click: function(cc,s){

         // var persons = [];
         // var compares = [];

         console.log(cc);
         console.log(s);
      

         if(this.compares.includes(s)){
         
            var a = this.compares.indexOf(s)

             this.compares.splice(a,1)

             this.compares.push(s)

             this.persons.splice(a,1)

             this.persons.push(cc)

              

         }else{

         this.compares.push(s);
         this.persons.push(cc);

        }

         console.log('----------------')

         console.log(this.compares);
         console.log(this.persons);



    },

    result: function() {

       
       var len = this.persons.length;

       console.log(len);

       for(var i = 0; i<len ; i++){

            

            var params = {
                 
                 name: this.persons[i],
                 gpa: this.compares[i]

            };


                axios.post("http://localhost:3000/api/mode",params).then(response => {

                                console.log(response.data);

                })


       }


    }
  },
  computed: {}
};
</script>
