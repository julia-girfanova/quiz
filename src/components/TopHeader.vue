<template>
  <header class="top-header">
    <div>
      <QuizPreview v-if="quiz" :quiz="quiz" />
    </div>
    <ThemeSwitcher @theme-changed="change_theme" />
  </header>
</template>

<script>
import QuizPreview from "./QuizPreview.vue";
import ThemeSwitcher from "./ThemeSwitcher.vue";

export default {
  components: {
    QuizPreview,
    ThemeSwitcher,
  },
  props: {
    quiz: Object,
  },
  methods: {
    change_theme(theme) {
      this.$emit("theme-changed", theme);
    },
  },
};
</script>

<style>
.top-header {
  height: 224px;
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: space-between;
  max-width: 1160px;
  margin: 0 auto;
  padding: 0px 64px;
}
@media (min-width: 768px) and (max-width: 1024px) {
  .top-header {
    height: 145px;
  }
}
@media (max-width: 768px) {
  .top-header {
    height: 72px;
    padding: 16px 24px 16px 24px;
  }
}
</style>
