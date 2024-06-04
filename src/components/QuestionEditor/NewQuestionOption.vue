<template>
  <div class="new-question-option">
    <div class="new-question-option__letter">{{ letter }}</div>
    <input
      class="new-question-option__text"
      placeholder="Вариант ответа"
      :value="text"
      @input="$emit('update:text', $event.target.value, number)"
    />
  </div>
</template>

<script>
export default {
  props: {
    number: Number,
    text: String,
  },
  computed: {
    letter() {
      const letters = ["A", "B", "C", "D"];
      return letters[this.number];
    },
  },
};
</script>

<style>
.new-question-option {
  background-color: var(--navy);
  margin-bottom: 20px;
  display: flex;
  border-radius: 24px;
  padding: 20px;
}
.new-question-option__letter {
  min-width: 56px;
  height: 56px;
  border-radius: 8px;
  background-color: var(--light-grey);
  font-size: 28px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 40px;
  color: var(--grey-navy);
}
.new-question-option__text {
  background-color: transparent;
  border: none;
  outline: none;
  color: var(--pure-white);
  font-size: 28px;
  font-family: Rubik;
  margin: 0px;
  text-align: left;
}
.option__text::placeholder {
  color: var(--light-blurish);
}
</style>
