<template>
  <div class="Questionnaire">
  	<pre>{{$route.params}}</pre>

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
  			firstName: '',
  			name: '',
  			society: '',
  		}
  	}
  },
  components: {
	Question
  }
}
</script>
