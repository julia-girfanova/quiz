<template>
  <div class="answer-options">
    <Option
      v-for="(option, idx) of options"
      :key="idx"
      :option="option"
      :option_number="idx"
      :selected_option="selected_option"
      :submitted_option="submitted_option"
      :answer="answer"
      :theme="theme"
      @option-selected="select_option"
    />
    <AnswerButton
      :selected_option="selected_option"
      :submitted_option="submitted_option"
      :is_quiz_ended="is_quiz_ended"
      @answer-submitted="submit_answer"
      @next-question-requested="next_question"
      @quiz-finished="finish_quiz"
    />
  </div>
</template>

<script>
import Option from "./Option.vue";
import AnswerButton from "./AnswerButton.vue";
export default {
  components: {
    Option,
    AnswerButton,
  },
  props: {
    options: Array,
    answer: Number,
    is_quiz_ended: Boolean,
    theme: String,
  },
  data() {
    return {
      selected_option: null,
      submitted_option: null,
    };
  },
  methods: {
    select_option(option_number) {
      this.selected_option = option_number;
    },
    submit_answer() {
      this.submitted_option = this.selected_option;
    },
    next_question() {
      let result = this.submitted_option === this.answer;
      this.$emit("next-question-requested", result);
      this.selected_option = null;
      this.submitted_option = null;
    },
    finish_quiz() {
      let result = this.submitted_option === this.answer;
      this.$emit("quiz-finished", result);
      this.selected_option = null;
      this.submitted_option = null;
    },
  },
};
</script>

<style>
.answer-options {
  width: 50%;
}

@media (min-width: 768px) and (max-width: 1024px) {
  .answer-options {
    width: 100%;
  }
}
@media (max-width: 768px) {
  .answer-options {
    width: 100%;
  }
}
</style>
