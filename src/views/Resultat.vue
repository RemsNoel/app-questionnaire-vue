<template>
  <div class="Resultat">
    <h1>Résultat</h1>    
    <div class="wrapper">
    	<div class="box a">
    		<!--Affichage du resulat avec le nom de l'utilisateur-->
    		<p>{{$route.params.rn_name}} {{$route.params.rn_firstName}} de la société {{$route.params.rn_society}}</p>
    		<p>Vous avez fait un score de :</p>
    		<h2>{{$route.params.rn_score}}/12</h2>
    <b-button type="submit" variant="primary" @click="rn_onSubmit">Retour à l'accueil</b-button>
    	</div>
    </div>
  </div>
</template>
<script>
  name: 'Resultat';
  export default {
  	methods: {
  		// Quand on clic sur le bouton Retour à l'accueil
  		rn_onSubmit(evt) {
        this.$router.push({ name: 'home'})
      },
  	}
  }

</script>