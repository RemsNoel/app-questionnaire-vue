<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div class="questionnaire">
  	<h1>App Questionnaire</h1>
  		<div class="wrapper">
	  		<div class="box a">Veuillez saisir Votre Prénom/Nom et le nom de votre Société</div>
	  		<div class="box b">B</div>
	  		<div class="box c">C</div>
	  		<div class="box d">D</div>
		</div>
  	<Question msg="Envoi de message vers Question"/>

<b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          required
          placeholder="Enter email"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Food:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.food"
          :options="foods"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-4">
        <b-form-checkbox-group v-model="form.checked" id="checkboxes-4">
          <b-form-checkbox value="me">Check me out</b-form-checkbox>
          <b-form-checkbox value="that">Check that out</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
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
        foods: [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
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
		  grid-template-rows: 1fr 1fr;
		  grid-gap: 5px;
		  background-color: #fff;
		  color: #444;
		  margin: 5px;
		}

		.box {
		  background-color: #444;
		  color: #fff;
		  border-radius: 5px;
		  /*padding: 20px;*/
		  font-size: 150%;
		}

		.a {
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