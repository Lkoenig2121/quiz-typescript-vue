<!-- eslint-disable vue/require-v-for-key -->
<script setup lang="ts">
    
    import { ref } from 'vue';

    const questions = [
        {
            "question": "What is Vue.js?",
            "answers": ["Programming language", "Javascript framework", "Server-side technology", "Operating system"],
            "correctAnswer": 'Javascript framework'
        },
        {
            "question": "Which of the following is NOT a feature of Vue.js?",
            "answers": ["Reactive data binding", "Virtual DOM", "Two-way data binding", "Server-side rendering"],
            "correctAnswer": "Server-side rendering"
        },
        {
            "question": "Which directive is used to conditionally render an element based on a given expression?",
            "answers": ["v-if", "v-for", "v-else", "v-bind"],
            "correctAnswer": "v-if"
        }
    ]

    const score = ref(0);
    const questionCount = ref(1);
    const selectedOption = ref("");
    const showScore = ref(false);
    const showRetry = ref(false)

    const selectedQuestion = ref(questions[0])

    const submitAnswer = () => {
        if (selectedQuestion.value.correctAnswer == selectedOption.value) {
            score.value++;
        }
        
        if (questionCount.value < questions.length) {
            selectedQuestion.value = questions[questionCount.value];
            questionCount.value++;
            selectedOption.value = ""
        } else {
            showScore.value = true;
            showRetry.value = true;
        }

    }

</script>

<template>
    <div class="wrapper">
        <form @submit.prevent="submitAnswer" v-if="!showScore">
            <div class="question">
                <div class="q"> {{ questionCount }} {{ selectedQuestion.question }} </div>
                <div class="option" v-for="(item, i) in selectedQuestion.answers">
                    <input type="radio" :id="`option${i}`" name="answers" v-model="selectedOption" :value="item">
                    <label :for="`option$[i]`">{{ item }}</label>
                </div>
                </div>
                <button type="submit">
                    submit
                </button>
        </form>
        <div class="scoreButton" v-else>
            <div class="score">
                score is {{ score }} out of {{ questions.length }}
            </div>
            <button class="button" onclick="window.location.reload()">Play again</button>
        </div>
    </div>
</template>

<style scoped>

.wrapper { 
      height: 300px;
      width: 400px;
      background-color: #fff;
      border-radius: 10px;
  }

  form {
      height: 100%;
      display: flex;
      flex-direction: column;
  }

  .question {
      flex: 1;
      padding: 1rem;
  }

  form > button { 
      background-color: #4273F4;
      border:none;
      padding: 1rem;
      color: #fff;
      font-size: 16px;
      letter-spacing: 1px;
      cursor: pointer;
  }

  .q {
      height: 40px;
  }

  .option {
      padding: 0.5em 0;
  }

  .scoreButton {
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 100%;
    align-items: center;
    justify-content: center;
  }
  /* .score { 
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
  } */

</style> 