<template>
  <div :class="['question', `question_${theme}`]">
    <p class="question__number">
      Вопрос {{ question_number + 1 }} из {{ quiz_length }}
    </p>
    <p class="question__text">
      {{ text }}
    </p>
    <div class="question__progress">
      <div class="question__slider" :style="{ width: `${progress}%` }"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    theme: String,
    text: String,
    question_number: Number,
    quiz_length: Number,
  },
  computed: {
    progress() {
      return ((this.question_number + 1) / this.quiz_length) * 100;
    },
  },
};
</script>

<style>
.question {
  width: 50%;
  justify-content: flex-start;
  padding-right: 100px;
}
.question__number {
  font-style: italic;
  font-family: Rubik;
  font-size: 20px;
  display: flex;
  align-items: center;
  font-weight: 300;
}
.question_light .question__number {
  color: var(--grey-navy);
}
.question_dark .question__number {
  color: var(--light-blurish);
}
.question__text {
  font-family: Rubik;
  font-size: 36px;
}
.question_light .question__text {
  color: var(--dark-navy);
}
.question_dark .question__text {
  color: var(--pure-white);
}
.question__progress {
  height: 16px;
  border-radius: 999px;
  display: flex;
  align-items: center;
  padding: 4px;
  box-sizing: border-box;
}
.question_light .question__progress {
  background-color: var(--pure-white);
}
.question_dark .question__progress {
  background-color: var(--navy);
}
.question__slider {
  width: 300px;
  height: 8px;
  background-color: var(--purple);
  border-radius: 104px;
  display: flex;
}
@media (min-width: 768px) and (max-width: 1024px) {
  .question {
    width: 100%;
    margin-bottom: 64px;
    padding-right: 0px;
  }
}
@media (max-width: 768px) {
  .question {
    width: 100%;
    margin-bottom: 40px;
    padding-right: 0px;
  }
  .question__text {
    font-size: 20px;
  }
  .question__number {
    font-size: 16px;
  }
}
</style>
