<template>
  <div class="Questionnaire">
  	<pre>{{formuser}}</pre>

  <Question/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Question from '@/components/Question.vue'

export default {
  name: 'Questionnaire',
  props:{
          firstName: String,
          name: String,
          society: String,
  },
  data () {
  	return {
  		formuser: {
  			firstName: this.firstName,
  			name: this.name,
  			society: this.society,
  		}
  	}
  },
  components: {
  	Question
  },
  
}
</script>
