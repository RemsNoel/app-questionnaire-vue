<template>
  <div class="Resultat">
  	<!-- <pre>{{$route.params.score}}</pre> -->
    <h1>Résultat</h1>    
    <div class="wrapper">
    	<div class="box a">
    		<h2>Score = {{$route.params.rn_score}}/12</h2>
    <b-button type="submit" variant="primary" @click="rn_onSubmit">Retour à l'accueil</b-button>
    	</div>
    </div>
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
<style lang="scss">
.wrapper {
		  display: grid;
		  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
		  grid-template-rows: 1fr;
		  grid-gap: 5px;
		  background-color: #fff;
		  color: #444;
		  margin: 5px;
		}

		.cellule {
			width: 85%;
			margin:auto;
		}

		.box {
		  background-color: #f4f5f7;
		  color: #000;
		  border-radius: 5px;
		  /*padding: 20px;*/
		  font-size: 150%;
		}

		.a{			
		  grid-column-start: 2;
	      grid-column-end: 5;
	      grid-row-start: 1;
	      grid-row-end: 1;
		}
</style>