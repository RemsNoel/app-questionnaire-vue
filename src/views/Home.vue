<template>
  <div class="home">
    <div>
    <div class="box">
  	<h1>App Questionnaire</h1>
  	</div>
<!-- Formulaire de rensignement des infos de l'utilisateur -->
<b-form @submit="rn_onSubmit" @reset="rn_onReset" v-if="show">
	<div class="wrapper">
	  		<div class="box a">Veuillez saisir Votre Prénom/Nom et le nom de votre Société</div>
	  		<div class="box b">
	  			<b-form-group
        id="input-group-1"
        label="Prénom:"
        label-for="input-1" class="cellule">
        <!-- Input du prenom -->
        <b-form-input class="cellule"
          id="input-1"
          v-model="form.rn_firstName"
          required
          placeholder="Prénom"
        ></b-form-input>
      </b-form-group>
  </div>
	  		<div class="box c">
	  			<b-form-group id="input-group-2" label="Nom:" label-for="input-2" class="cellule">
	  	<!-- Input du nom -->
        <b-form-input
          id="input-2"
          v-model="form.rn_name"
          required
          placeholder="Nom"
        ></b-form-input>
      </b-form-group>
  </div>
	  		<div class="box d">
	  			<b-form-group id="input-group-3" label="Société:" label-for="input-3" class="cellule">
	  	<!-- input de la société -->
        <b-form-input 
          id="input-3"
          v-model="form.rn_society"
          required
          placeholder="Société">          	
          </b-form-input>
      </b-form-group>
  </div>
		</div>
		<!-- Les boutons submit et reset -->
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger" class="buttrn_onreset">Reset</b-button>
    </b-form>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'home',
  components: {
  },
  data() {
      return {
      	// les infos que l'on transmettra a la page suivante
        form: {
          rn_firstName: '',
          rn_name: '',
          rn_society: '',
        },
        show: true
      }
    },
    methods: {
    	// methode appelé quand on appuie sur le bouton submit
      rn_onSubmit(evt) {
        evt.preventDefault()
        // on push en paramatre le prenom/nom/société
        this.$router.push({ name: 'questionnaire', params: this.form})
      },
      	// methode appelé quand on appuie sur le bouton reset
      rn_onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.rn_firstName = ''
        this.form.rn_name = ''
        this.form.rn_society = ''
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
}
</script>
<style lang="scss">
	body{
		background-image:url(../assets/tunnel.jpg);		
  		background-position: center;
	}
		/*Création d'une grille pour la page */
		.wrapper {
		  display: grid;
		  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
		  grid-template-rows: 1fr 2fr;
		  grid-gap: 5px;
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

		.a {
	        grid-column-start: 2;
	        grid-column-end: 5;
	        grid-row-start: 1;
	        grid-row-end: 2;
	    }

		.b {
	        grid-column-start: 2;
	        grid-column-end: 3;
	        grid-row-start: 2;
	        grid-row-end: 2;
	    }

		.c {
	        grid-column-start: 3;
	        grid-column-end: 4;
	        grid-row-start: 2;
	        grid-row-end: 2;
	    }

		.d {
	        grid-column-start: 4;
	        grid-column-end: 5;
	        grid-row-start: 2;
	        grid-row-end: 2;
	    }

	    .f {
	        grid-column-start: 2;
	        grid-column-end: 5;
	        grid-row-start: 1;
	        grid-row-end: 2;
	    }

	    .buttrn_onreset {
	    	margin-left : 5px;
	    }
</style>
