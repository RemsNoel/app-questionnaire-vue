<template>
  <div class="Question">
  	<div classe="wrapper">
  	<h2>Questionnaire</h2>
  	<div class="box a">
  		<!-- affichage de l'enoncé -->
    	<b-form-group :label="questions[i].enoncer" >    	
    	<!-- affichage des différentes réponses proposés -->
      	<b-form-radio  v-for="reponse in questions[i].reponses" v-model="rn_selected" name="some-radios" v-bind:value="reponse">{{reponse}}</b-form-radio>
      	</b-form-radio-group>
    
      	<!-- on affiche le choix selectionné -->
    	<div class="mt-3">Selected: <strong>{{ rn_selected }}</strong></div>
    	<!-- bouton pour envoyer la réponse -->
    	<b-button type="submit" variant="primary" @click="rn_onSubmit">Question Suivante</b-button>
    </b-form-group>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'Question',
  data() {
  	return {
  		// quand on fait un choix on sauvegarde la valeur ici
  		rn_selected :'',
  		// tableau des differentes questions
  		questions : {},
  		i:0,
  		// les informations qui seront envoyer à la page résultat
  		form: {
          rn_firstName: this.$route.params.rn_firstName,
          rn_name: this.$route.params.rn_name,
          rn_society: this.$route.params.rn_society,
  		  rn_score:0,
        },
  	}
  },
  // methods appelé a la création de la page
  created: function(){
  	this.fetchData()

  },
  methods: {
  	// méthode pour récupéer le JSON des questions
  	fetchData: function(){
  		this.questions = require("../assets/questions.json");

  	// console.log(this.questions)
  	},
  	// opérations faites quand on click sur le bouton Question suivante
  	rn_onSubmit(evt) {
  		// Si la réponse correspond a celle dans le Json, on donne un point
  		if ( this.rn_selected == this.questions[this.i].correction) {
  			this.form.rn_score++;
  		}
  		// on oblige la séléction d'une réponse pour pouvoir allez a la suivante
  		if (this.rn_selected != '') {
  			// si on est pas a la derniere question
  			if (this.i < 11) {
        	this.i++
    		} else {
    		// si on est a la derniere question on passe a la page résultat
    			this.$router.push({ name: 'resultat', params: this.form})
    		}
    	}
    	// on remet la selection a vide pour la question suivante
    	this.rn_selected='';
     },
  }
}
</script>