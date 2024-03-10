<template>
  <div class="quiz-preview">
    <img
      class="quiz-preview__icon"
      :src="quiz.icon"
      :style="{ 'background-color': quiz.icon_background }"
    />
    <p class="quiz-preview__name">{{ quiz.name }}</p>
  </div>
</template>

<script>
export default {
  props: {
    quiz: Object,
  },
};
</script>

<style>
.quiz-preview {
  cursor: pointer;
  display: flex;
  flex-direction: row;
  align-items: center;
  box-sizing: border-box;
}
.quiz-preview__icon {
  height: 56px;
  width: 56px;
  box-sizing: border-box;
  border-radius: 8px;
  margin-right: 32px;
}
.quiz-preview__name {
  font-size: 28px;
  font-weight: 500;
  margin: 0px;
}
@media (max-width: 768px) {
  .quiz-preview__name {
    font-size: 18px;
  }
  .quiz-preview__icon {
    height: 40px;
    width: 40px;
    margin-right: 16px;
  }
}
</style>
