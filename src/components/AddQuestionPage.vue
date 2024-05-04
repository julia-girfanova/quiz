<template>
  <div class="add-question-page">
    <div class="add-question__text">
      <textarea
        class="add-question__textarea"
        placeholder="Текст вопроса"
      ></textarea>
    </div>
    <div class="add-question__options">
      <div class="add-question__option">
        <div class="option__letter">A</div>
        <input class="option__text" placeholder="Вариант ответа" />
      </div>
      <div class="add-question__option">
        <div class="option__letter">B</div>
        <input class="option__text" placeholder="Вариант ответа" />
      </div>
      <div class="add-question__option">
        <div class="option__letter">C</div>
        <input class="option__text" placeholder="Вариант ответа" />
      </div>
      <div class="add-question__option">
        <div class="option__letter">D</div>
        <input class="option__text" placeholder="Вариант ответа" />
      </div>
      <button class="add-question__save">Сохранить вопрос</button>
    </div>
  </div>
</template>

<script>
export default {};
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
}
.add-question__options {
  flex-grow: 1;
}
.add-question__option {
  background-color: var(--navy);
  margin-bottom: 20px;
  display: flex;
  border-radius: 24px;
  padding: 20px;
}
.option__text {
  background-color: transparent;
  border: none;
  outline: none;
  color: var(--pure-white);
}
.option__text::placeholder {
  color: var(--light-blurish);
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
}
</style>
