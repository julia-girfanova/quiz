<template>
  <div class="results">
    <h2 class="results__title">
      Квиз окончен
      <span class="results__title_bold">ты набрал...</span>
    </h2>
    <div class="results__block">
      <div :class="['score', `score_${theme}`]">
        <QuizPreview :quiz="quiz" />
        <p class="score__number">{{ score }}</p>
        <p class="score__summary">из {{ quiz.questions.length }}</p>
      </div>
      <button class="results__button" @click="restart">Играть снова</button>
    </div>
  </div>
</template>

<script>
import QuizPreview from "./QuizPreview.vue";
export default {
  components: {
    QuizPreview,
  },
  props: {
    quiz: Object,
    score: Number,
    theme: String,
  },
  methods: {
    restart() {
      this.$emit("restart");
    },
  },
};
</script>

<style>
.results {
  max-width: 1160px;
  margin: 0 auto;
  display: flex;
  padding: 0px 64px 64px 64px;
}
.results__title {
  font-size: 64px;
  font-family: Rubik;
  font-weight: 300;
  width: 50%;
  margin: 0px;
}
.results__title_bold {
  font-size: 64px;
  font-family: Rubik;
  font-weight: 500;
  display: block;
}
.results__button {
  background-color: var(--purple);
  width: 100%;
  height: 92px;
  border-radius: 24px;
  cursor: pointer;
  display: flex;
  font-size: 28px;
  color: var(--pure-white);
  justify-content: center;
  align-items: center;
  border: transparent;
}
.results__block {
  width: 50%;
}
.score {
  border-radius: 24px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 48px;
  margin-bottom: 32px;
}
.score_light {
  background-color: var(--pure-white);
}
.score_dark {
  background-color: var(--navy);
}
.score__number {
  font-size: 144px;
  font-weight: 500;
  font-family: Rubik;
  margin: 0px;
}
.score_light .score__number {
  color: var(--dark-navy);
}
.score_dark .score__number {
  color: var(--pure-white);
}
.score__summary {
  font-size: 24px;
  font-weight: 200;
  font-family: Rubik;
  margin: 0;
}
.score_light .score__summary {
  color: var(--grey-navy);
}
.score_dark .score__summary {
  color: var(--light-blurish);
}
@media (min-width: 768px) and (max-width: 1024px) {
  .results {
    flex-direction: column;
  }
  .results__title {
    width: 100%;
  }
  .results__block {
    width: 100%;
  }
  .score {
    margin-top: 64px;
  }
}
@media (max-width: 768px) {
  .results {
    flex-direction: column;
    padding: 0px 24px 24px 24px;
  }
  .results__title {
    width: 100%;
    font-size: 40px;
  }
  .results__block {
    width: 100%;
  }
  .score {
    margin-top: 40px;
    border-radius: 12px;
  }
  .results__title_bold {
    font-size: 40px;
  }
  .score__number {
    font-size: 88px;
  }
  .score__summary {
    font-size: 18px;
  }
  .results__button {
    height: 56px;
    font-size: 18px;
    border-radius: 12px;
  }
}
</style>
