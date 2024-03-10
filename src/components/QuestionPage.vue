<template>
  <div class="question-page">
    <Question
      :text="question.text"
      :question_number="question_number"
      :quiz_length="quiz.questions.length"
      :theme="theme"
    />
    <AnswerOptions
      :options="question.options"
      :answer="question.answer"
      :is_quiz_ended="is_quiz_ended"
      :theme="theme"
      @next-question-requested="increment_question_number"
      @quiz-finished="finish_quiz"
    />
  </div>
</template>

<script>
import Question from "./Question.vue";
import AnswerOptions from "./AnswerOptions.vue";
export default {
  components: {
    Question,
    AnswerOptions,
  },
  props: {
    quiz: Object,
    theme: String,
  },
  data() {
    return {
      question_number: 0,
      score: 0,
    };
  },
  computed: {
    question() {
      return this.quiz.questions[this.question_number];
    },
    is_quiz_ended() {
      return this.question_number + 1 === this.quiz.questions.length;
    },
  },
  methods: {
    increment_question_number(result) {
      this.question_number = this.question_number + 1;
      if (result) {
        this.score = this.score + 1;
      }
    },
    finish_quiz(result) {
      if (result) {
        this.score = this.score + 1;
      }
      this.$emit("quiz-finished", this.score);
      this.question_number = 0;
    },
  },
};
</script>

<style>
.question-page {
  display: flex;
  justify-content: center;
  max-width: 1160px;
  margin: 0 auto;
  padding: 0px 64px 64px 64px;
}
@media (min-width: 768px) and (max-width: 1024px) {
  .question-page {
    flex-direction: column;
  }
}
@media (max-width: 768px) {
  .question-page {
    flex-direction: column;
    padding: 0px 24px 24px 24px;
  }
}
</style>
