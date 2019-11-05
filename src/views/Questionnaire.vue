<template>
  <div class="Questionnaire">
  	<!-- Affichage des Questions -->
  <Question/>
  </div>
</template>

<script>
import Question from '@/components/Question.vue'

export default {
  name: 'Questionnaire',
  components: {
	Question
  }
}
</script>
