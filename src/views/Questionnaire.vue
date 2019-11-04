<template>
  <div class="Questionnaire">
  <Question/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Question from '@/components/Question.vue'

export default {
  name: 'Questionnaire',
  components: {
	Question
  }
}
</script>
