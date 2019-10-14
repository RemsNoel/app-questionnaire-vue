<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div class="questionnaire">
  	<h1>App Questionnaire</h1>
  		

<b-form @submit="onSubmit" @reset="onReset" v-if="show">
	<div class="wrapper">
	  		<div class="box a">Veuillez saisir Votre Prénom/Nom et le nom de votre Société</div>
	  		<div class="box b">
	  			<b-form-group
        id="input-group-1"
        label="Prénom:"
        label-for="input-1" class="cellule">
        <b-form-input class="cellule"
          id="input-1"
          v-model="form.firstName"
          required
          placeholder="Enter FirsName"
        ></b-form-input>
      </b-form-group>
  </div>
	  		<div class="box c">
	  			<b-form-group id="input-group-2" label="Nom:" label-for="input-2" class="cellule">
        <b-form-input
          id="input-2"
          v-model="form.name"
          required
          placeholder="Enter Name"
        ></b-form-input>
      </b-form-group>
  </div>
	  		<div class="box d">
	  			<b-form-group id="input-group-3" label="Nom Société:" label-for="input-3" class="cellule">
        <b-form-input 
          id="input-3"
          v-model="form.food"
          required
          placeholder="Enter Society">          	
          </b-form-input>
      </b-form-group>
  </div>
		</div>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <!-- <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card> -->
  	<Question msg="Envoi de message vers Question"/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Question from '@/components/Question.vue'

export default {
  name: 'questionnaire',
  components: {
    Question
  },
  data() {
      return {
        form: {
          email: '',
          name: '',
          food: null,
          checked: []
        },
        show: true
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.email = ''
        this.form.name = ''
        this.form.food = null
        this.form.checked = []
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
		.wrapper {
		  display: grid;
		  grid-template-columns: 1fr 1fr 1fr;
		  grid-template-rows: 1fr 2fr;
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

		.a {
			background-color: #007bff;
	        grid-column-start: 1;
	        grid-column-end: 4;
	        grid-row-start: 1;
	        grid-row-end: 2;
	    }

		.b {
	        grid-column-start: 1;
	        grid-column-end: 2;
	        grid-row-start: 2;
	        grid-row-end: 2;
	    }

		.c {
	        grid-column-start: 2;
	        grid-column-end: 3;
	        grid-row-start: 2;
	        grid-row-end: 2;
	    }

		.d {
	        grid-column-start: 3;
	        grid-column-end: 4;
	        grid-row-start: 2;
	        grid-row-end: 2;
	    }
</style>