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
    <button
      v-if="selected_option !== null && submitted_option === null"
      class="answer-options__button"
      @click="submit_answer"
    >
      Подтвердить ответ
    </button>
    <button v-if="selected_option === null" class="answer-options__button">
      Выберите ответ
    </button>
    <button
      v-if="submitted_option !== null && !is_quiz_ended"
      class="answer-options__button"
      @click="next_question"
    >
      Следующий вопрос
    </button>
    <button
      v-if="submitted_option !== null && is_quiz_ended"
      class="answer-options__button"
      @click="finish_quiz"
    >
      Завершить квиз
    </button>
  </div>
</template>

<script>
import Option from "./Option.vue";
export default {
  components: {
    Option,
  },
  props: {
    options: Array,
    answer: Number,
    is_quiz_ended: Boolean,
    theme: String,
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
  data() {
    return {
      selected_option: null,
      submitted_option: null,
    };
  },
};
</script>

<style>
.answer-options {
  width: 50%;
}

.answer-options__button {
  background-color: var(--purple);
  height: 92px;
  border-radius: 24px;
  cursor: pointer;
  display: flex;
  font-size: 28px;
  color: var(--pure-white);
  justify-content: center;
  align-items: center;
  border: transparent;
  width: 100%;
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
  .answer-options__button {
    height: 56px;
    font-size: 18px;
    border-radius: 12px;
  }
}
</style>
