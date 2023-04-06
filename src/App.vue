<template>

  <div id="app">

    <h1> Would you rather...</h1>

    <ul>
      <li v-for="question in questions" :key="question.id">
        <would-you-ratherr 
        :question="question.question" 
        :answer1="question.answer1"
        :answer2=question.answer2 
        @answer-selected="answerSelected">
        </would-you-ratherr>
      </li>
    </ul>

    <p>{{ userSelectionMessage }}</p>

    <ul>
      <li v-for="(selection, id) in userSelectionMessage" :key="id">
      Question {{ id }}: {{ selection }}</li>
    </ul>

  </div>


</template>

<script>
import WouldYouRatherr from './components/WouldYouRatherr.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherr
  },
  data() {
    return {
      questions: [
        {
          id: 0,
          question: 'Would you rather do school work as a group or by yourself?',
          answer1: 'As a group',
          answer2: 'By yourself',
        },
        {
          id: 1,
          question: 'Would you rather it be warm and raining or cold and snowing today?',
          answer1: 'Warm and raining',
          answer2: 'Cold and snowing',
        },
        {
          id: 2,
          question: 'Would you rather eat a popsicle or a cupcake?',
          answer1: 'Eat a popsicle',
          answer2: 'A cupcake',
        }
      ]
    }
  },
  methods: {
    answerSelected({ id, choice }) {
      this.userSelectionMessage= 'Thanks! you chose ${choice}';
    }
  }
}

</script>

<style>

body {
  background: gray ;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: peachpuff;
  box-shadow: 1 2px 3px rgba(0,0,0,0);
}


</style>
