<template>
  <div class="start">
    <div :class="['welcome', `welcome_${theme}`]">
      <h1 class="welcome__title">
        Welcome to the
        <span class="welcome__title_bold">Frontend Quiz!</span>
      </h1>
      <p class="welcome__advice">Pick a subject to get started.</p>
    </div>
    <div class="quiz-list">
      <div
        :class="['quiz-list__item', `quiz-list__item_${theme}`]"
        v-for="quiz in quiz_list"
        :key="quiz.name"
        @click="select(quiz.id)"
      >
        <QuizPreview :quiz="quiz" />
      </div>
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
    quiz_list: Array,
    theme: String,
  },
  methods: {
    select(quiz_id) {
      this.$emit("quiz-selected", quiz_id);
    },
  },
};
</script>

<style>
.start {
  display: flex;
  max-width: 1160px;
  margin: 0 auto;
  padding: 0px 64px 64px 64px;
}
.welcome {
  width: 50%;
}
.welcome__title {
  font-weight: 300;
  font-size: 64px;
  margin: 0px;
}
.welcome_light .welcome__title {
  color: var(--dark-navy);
}
.welcome_dark .welcome__title {
  color: var(--pure-white);
}
.welcome__title_bold {
  display: block;
  font-weight: 500;
}
.welcome__advice {
  font-weight: 300;
  font-style: italic;
  font-size: 20px;
  margin: 48px 0 0 0;
}
.welcome_light .welcome__advice {
  color: var(--grey-navy);
}
.welcome_dark .welcome__advice {
  color: var(--light-blurish);
}
.quiz-list__item {
  border-radius: 24px;
  cursor: pointer;
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 24px;
  padding: 20px;
  box-sizing: border-box;
}
.quiz-list__item_dark {
  background-color: var(--navy);
}
.quiz-list__item_light {
  background-color: var(--pure-white);
}

.quiz-list__item:last-child {
  margin-bottom: 0px;
}

.quiz-list {
  width: 50%;
}
@media (min-width: 768px) and (max-width: 1024px) {
  .start {
    flex-direction: column;
  }
  .welcome {
    width: 100%;
  }
  .welcome__advice {
    margin: 16px 0 0 0;
  }
  .quiz-list {
    width: 100%;
    margin-top: 64px;
  }
}
@media (max-width: 768px) {
  .start {
    flex-direction: column;
    padding: 0px 24px 24px 24px;
  }
  .welcome {
    width: 100%;
  }
  .welcome__title {
    font-size: 40px;
  }
  .welcome__advice {
    margin: 16px 0 0 0;
    font-size: 14px;
  }
  .quiz-list {
    width: 100%;
    margin-top: 40px;
  }
  .quiz-list__item {
    border-radius: 12px;
  }
}
</style>
