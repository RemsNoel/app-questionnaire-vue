<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div class="Question">
  	<h2>Question template</h2>
  	<!-- <p>{{ form }}</p> -->
  	<div>
    <b-form-group>
    	{{questions[i].ennoncer}}
      <b-form-radio  v-for="reponse in questions[i].reponses" v-model="selected" name="some-radios" v-bind:value="reponse">{{reponse}}</b-form-radio>
      </b-form-radio-group>
    </b-form-group>
    

    <div class="mt-3">Selected: <strong>{{ selected }}</strong></div>
    <b-button type="submit" variant="primary">Question Suivante</b-button>
  </div>

  <!-- <pre>{{questions}}</pre> -->
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Question',
  data() {
  	return {
  		selected :'',
  		questions : {},
  		i:0,
  	}
  },
  created: function(){
  	this.fetchData()
  	console.log()

  },
  methods: {
  	fetchData: function(){
  		this.questions = require("../assets/questions.json");
  	},
  }
}
</script>