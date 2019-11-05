<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div class="Question">
  	<div classe="wrapper">
  	<!-- <pre>{{$route.params}}</pre> -->
  	<h2>Questionnaire</h2>
  	<!-- <p>{{ form }}</p> -->
  	<div class="box a">
    	<b-form-group :label="questions[i].ennoncer" >    	

      	<b-form-radio  v-for="reponse in questions[i].reponses" v-model="rn_selected" name="some-radios" v-bind:value="reponse">{{reponse}}</b-form-radio>
      	</b-form-radio-group>
    

    	<div class="mt-3">Selected: <strong>{{ rn_selected }}</strong></div>
    	<b-button type="submit" variant="primary" @click="rn_onSubmit">Question Suivante</b-button>
    </b-form-group>
  </div>
  <!-- <h1> Score = {{rn_score}}</h1> -->
  <!-- <pre>{{form}}</pre> -->
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Question',
  data() {
  	return {
  		rn_selected :'',
  		questions : {},
  		i:0,
  		form: {
          rn_firstName: this.$route.params.rn_firstName,
          rn_name: this.$route.params.rn_name,
          rn_society: this.$route.params.rn_society,
  		  rn_score:0,
        },
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
  	rn_onSubmit(evt) {
  			// console.log(this.questions[this.i]);
  		if ( this.rn_selected == this.questions[this.i].correction) {
  			this.form.rn_score++;
  		}
  		if (this.rn_selected != '') {
  			if (this.i < 11) {
        	this.i++
    		} else {
    			this.$router.push({ name: 'resultat', params: this.form})
    		}
    	}
    	this.rn_selected='';
        // alert(JSON.stringify(this.form))
     },
  }
}
</script>