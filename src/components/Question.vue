<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div class="Question">
  	<pre>{{$route.params}}</pre>
  	<h2>Questionnaire</h2>
  	<!-- <p>{{ form }}</p> -->
  	<div>
    <b-form-group :label="questions[i].ennoncer" >    	

      <b-form-radio  v-for="reponse in questions[i].reponses" v-model="selected" name="some-radios" v-bind:value="reponse">{{reponse}}</b-form-radio>
      </b-form-radio-group>
    </b-form-group>
    

    <div class="mt-3">Selected: <strong>{{ selected }}</strong></div>
    <b-button type="submit" variant="primary" @click="onSubmit">Question Suivante</b-button>
  </div>
  <!-- <h1> Score = {{score}}</h1> -->
  <!-- <pre>{{questions[i]}}</pre> -->
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
  		score:0,
  	}
  },
  created: function(){
  	this.fetchData()

  },
  methods: {
  	fetchData: function(){
  		this.questions = require("../assets/questions.json");

  	// console.log(this.questions)
  	},
  	onSubmit(evt) {
  			// console.log(this.questions[this.i]);
  		if ( this.selected == this.questions[this.i].correction) {
  			this.score++;
  		}
  		if (this.selected != '') {
  			if (this.i < 11) {
        	this.i++
    		} else {
    			
    		}
    	}
    	this.selected='';
        // alert(JSON.stringify(this.form))
     },
  }
}
</script>