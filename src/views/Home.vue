<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <Questionnaire/>
  </div>
</template>

<script>
// @ is an alias to /src
import Questionnaire from '@/views/Questionnaire.vue'

export default {
  name: 'home',
  components: {
    Questionnaire
  }
}
</script>
