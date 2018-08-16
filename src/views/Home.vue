
<template>
  <div class="home">
    
<!-- Carousel -->

  <h1>Questions</h1>
  <br>
  <ol>
    <li v-for="surveyItem in surveyItems">
      <h6>{{surveyItem.question}}</h6>
      <span v-for="choice in choices">
        <input type="radio" v-bind:value="choice" v-model="surveyItem.answer"> 
        <label> {{ choice }} </label> | 
      </span>
    </li>
  </ol>


 <router-link :to="{ name: 'second_page', params: { id: 12  }}">
   <button v-on:click="submit()">Submit</button>
 </router-link>
  <!--  hello -->
  </div>
</template>

<style>


</style>

<script>
export default {
  data: function() {
    return {
      message: "Vishnu is an american Computer Programmer",
      choices: [
        "Vishnu",
        "Vamsi",
        "Naveen",
        "Adi",
        "Ganesh",
        "Lokesh",
        "Sachwin",
        "Siddarth"
      ],
      surveyItems: [
        {question: "Who is the most Handsome Guy in the Group?", answer: ""},
        {question: "Who's Belly is most cutest?", answer: ""},
        {question: "Who has the most Blackest Soothu?", answer: ""},
        {question: "Who is the most Unluckiest person in the group?", answer: ""},
        {question: "Who is the most Luckiest Person in the group?", answer: ""},
        {question: "Who is the most intelligent Person in the group?", answer: ""}
      ]
      
    };
  },
  created: function() {},
  methods: {
    submit: function() {


      var ans = [];
      
      this.choices.forEach(function(choice) {

        var count = 0;

        this.surveyItems.forEach(function(sur) {

          if (choice === sur.answer) {

            count += 1;
          }


        }.bind(this));

        var anss = choice + "'s score:" + count;
        ans.push(anss); 

      }.bind(this));

      console.log(ans);


    }

  },
  computed: {

  }
};
</script>