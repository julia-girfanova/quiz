<template>
  <div class="add-question-page">
    <div class="add-question__text">
      <textarea
        class="add-question__textarea"
        placeholder="Текст вопроса"
      ></textarea>
    </div>
    <div class="add-question__options">
      <NewQuestionOption
        v-for="(option, index) of options"
        :key="index"
        :number="index"
        :text="option"
        @update:text="update_option_text"
      />
      <button class="add-question__save">Сохранить вопрос</button>
    </div>
  </div>
</template>

<script>
import NewQuestionOption from "./QuestionEditor/NewQuestionOption.vue";
export default {
  components: {
    NewQuestionOption,
  },
  data() {
    return {
      options: ["1111", "", "3", ""],
    };
  },
  methods: {
    update_option_text(text, number) {
      this.options[number] = text;
    },
  },
};
</script>

<style>
.add-question-page {
  max-width: 1160px;
  display: flex;
  margin: 0 auto;
  gap: 90px;
  padding: 0px 64px 64px 64px;
}
.add-question__text {
  flex-grow: 1;
  flex-basis: 535px;
}
.add-question__options {
  flex-grow: 1;
  flex-basis: 535px;
}

.add-question__save {
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
.add-question__textarea {
  background-color: var(--navy);
  border-radius: 24px;
  width: 100%;
  color: var(--pure-white);
  resize: none;
  height: 440px;
  border: none;
  font-family: Rubik;
  padding: 20px;
  outline: none;
  font-size: 28px;
}
.add-question__textarea::placeholder {
  color: var(--light-blurish);
  font-size: 28px;
}
</style>
