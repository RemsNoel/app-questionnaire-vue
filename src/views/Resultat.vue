<template>
  <div class="Resultat">
  	<!-- <pre>{{$route.params.score}}</pre> -->
    <h1>Résultat</h1>
    <h2>Score = {{$route.params.rn_score}}/12</h2>
    <b-button type="submit" variant="primary" @click="rn_onSubmit">Retour à l'accueil</b-button>
  </div>
</template>
<script>
  name: 'Resultat';
  export default {
  	methods: {
  		rn_onSubmit(evt) {
        this.$router.push({ name: 'home'})
        // alert(JSON.stringify(this.form))
      },
  	}
  }

</script>