<template>
  <button
    v-if="selected_option !== null && submitted_option === null"
    class="answer-button"
    @click="$emit('answer-submitted')"
  >
    Подтвердить ответ
  </button>
  <button v-if="selected_option === null" class="answer-button">
    Выберите ответ
  </button>
  <button
    v-if="submitted_option !== null && !is_quiz_ended"
    class="answer-button"
    @click="$emit('next-question-requested')"
  >
    Следующий вопрос
  </button>
  <button
    v-if="submitted_option !== null && is_quiz_ended"
    class="answer-button"
    @click="$emit('quiz-finished')"
  >
    Завершить квиз
  </button>
</template>

<script>
export default {
  props: {
    selected_option: Number,
    submitted_option: Number,
    is_quiz_ended: Boolean,
  },
};
</script>

<style>
.answer-button {
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
@media (max-width: 768px) {
  .answer-button {
    height: 56px;
    font-size: 18px;
    border-radius: 12px;
  }
}
</style>
