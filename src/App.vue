<template>
  <div :class="['app', `app_${theme}`]">
    <TopHeader :quiz="quiz" @theme-changed="change_theme" />
    <StartPage
      v-if="page === 'StartPage'"
      :theme="theme"
      :quiz_list="quiz_list"
      @quiz-selected="select_quiz"
    />
    <QuestionPage
      v-if="page === 'QuestionPage'"
      :quiz="quiz"
      :theme="theme"
      @quiz-finished="show_results"
    />
    <ResultsPage
      v-if="page === 'ResultsPage'"
      :score="score"
      :quiz="quiz"
      :theme="theme"
      @restart="restart"
    />
  </div>
</template>

<script>
import TopHeader from "./components/TopHeader.vue";
import StartPage from "./components/StartPage.vue";
import QuestionPage from "./components/QuestionPage.vue";
import ResultsPage from "./components/ResultsPage.vue";

export default {
  components: {
    TopHeader,
    StartPage,
    QuestionPage,
    ResultsPage,
  },
  data() {
    return {
      quiz_id: null,
      quiz_list: [
        {
          id: "the_sopranos",
          name: "Клан Сопрано",
          icon: "/icon-sopranos.jpeg",
          icon_background: "#e0fdef",
          questions: [
            {
              text: "Кто из этих людей стал стучать на мафию?",
              options: [
                "Дженис Сопрано",
                "Джонни Сек",
                "Сальваторе Банпеньсьеро",
                "Петси Парисси",
              ],
              answer: 2,
            },
            {
              text: "Кто убил Ричи Априла?",
              options: [
                "Тони Сопрано",
                "Кристофер Молтисанти",
                "Дженис Сопрано",
                "Джуниор Сопрано",
              ],
              answer: 2,
            },
          ],
        },
      ],
      theme: "light",
      page: "StartPage",
      score: 0,
    };
  },
  computed: {
    quiz() {
      return this.quiz_list.find((q) => q.id === this.quiz_id);
    },
  },
  methods: {
    select_quiz(quiz_id) {
      this.quiz_id = quiz_id;
      this.page = "QuestionPage";
    },
    change_theme(theme) {
      this.theme = theme;
    },
    show_results(score) {
      this.score = score;
      this.page = "ResultsPage";
    },
    restart() {
      this.page = "StartPage";
      this.quiz_id = null;
    },
  },
};
</script>

<style>
@import "./styles/fonts.css";
@import "./styles/variables.css";

body {
  font-family: Rubik;
  margin: 0px;
}
.app {
  min-height: 100vh;
}
.app_light {
  background-image: url(/pattern-background-desktop-light.svg);
  background-color: #f4f6fa;
  background-size: cover;
  color: #313e51;
}
.app_dark {
  background-image: url(/pattern-background-desktop-dark.svg);
  background-color: #313e51;
  background-size: cover;
  color: white;
}
</style>
