<template>
  <div class="create-quiz-page">
    <div class="new-quiz">
      <div class="quiz-info">
        <NewQuizLogo />
        <input class="quiz-info__name" placeholder="Введите нажвание" />
      </div>
      <button class="new-quiz__save">Сохранить опрос</button>
    </div>
    <div class="questions">
      <div class="questions__summary">
        <p class="questions__count">0 вопросов</p>
        <button class="questions__add">
          <img class="questions__plus" src="/plus.svg" />
        </button>
      </div>
      <div class="questions__item">
        <p class="questions__text">Какая шабака жгила мою кашу?</p>
        <div class="questions__add"></div>
      </div>
    </div>
  </div>
</template>

<script>
import NewQuizLogo from "./NewQuizLogo.vue";
export default {
  components: {
    NewQuizLogo,
  },
};
</script>

<style>
.create-quiz-page {
  margin: 0 auto;
  display: block;
  max-width: 1160px;
}
.new-quiz {
  display: flex;
  width: 100%;
}
.quiz-info {
  width: 50%;
  border-radius: 24px;
  background-color: var(--navy);
  display: flex;
  padding: 20px;
}

.quiz-info__name {
  background-color: transparent;
  border: none;
  font-size: 28px;
  color: var(--pure-white);
  margin-left: 30px;
  outline: none;
}
.quiz-info__name::placeholder {
  color: var(--light-blurish);
}

.questions__plus {
  width: 30px;
  height: 30px;
}
.new-quiz__save {
  width: 50%;
  border-radius: 24px;
  margin-left: 30px;
  background-color: var(--purple);
  border: none;
  font-size: 28px;
  color: var(--pure-white);
  cursor: pointer;
}
.questions {
  margin-top: 30px;
}
.questions__summary {
  display: flex;
  background-color: var(--navy);
  border-radius: 24px;
  padding: 20px;
  justify-content: space-between;
  align-items: center;
}
.questions__add {
  border-radius: 8px;
  width: 56px;
  height: 56px;
  background-color: var(--pure-white);
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  cursor: pointer;
}
.questions__count {
  margin: 0px;
  font-size: 28px;
  font-weight: 300;
}
.questions__item {
  display: flex;
  background-color: var(--navy);
  border-radius: 24px;
  margin-top: 30px;
  padding: 20px;
  justify-content: space-between;
  align-items: center;
}
.questions__text {
  font-size: 28px;
  font-weight: 300;
  margin: 0;
}
</style>
