<template>
  <button
    :class="{
      option: true,
      [`option_${theme}`]: true,
      option_selected: option_number === selected_option,
      option_correct: is_correct,
      option_incorrect: is_incorrect,
    }"
    @click="select"
  >
    <div class="option__letter">{{ letter }}</div>
    <p class="option__text">{{ option }}</p>
    <img v-if="is_correct" class="option__icon" src="/icon-correct.svg" />
    <img v-if="is_incorrect" class="option__icon" src="/icon-incorrect.svg" />
  </button>
</template>

<script>
export default {
  props: {
    option: String,
    option_number: Number,
    selected_option: Number,
    submitted_option: Number,
    answer: Number,
    theme: String,
  },
  methods: {
    select() {
      this.$emit("option-selected", this.option_number);
    },
  },
  computed: {
    letter() {
      let letters = ["A", "B", "C", "D"];
      return letters[this.option_number];
    },
    is_correct() {
      return (
        this.option_number === this.answer && this.submitted_option !== null
      );
    },
    is_incorrect() {
      if (this.submitted_option !== null) {
        return (
          this.option_number === this.submitted_option &&
          this.option_number !== this.answer
        );
      }
      return false;
    },
  },
};
</script>

<style>
.option {
  border-radius: 24px;
  display: flex;
  margin-bottom: 24px;
  padding: 20px;
  align-items: center;
  width: 100%;
  border: 3px solid transparent;
  cursor: pointer;
}
.option_light {
  background-color: var(--pure-white);
}
.option_dark {
  background-color: var(--navy);
}
.option__letter {
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
.option__text {
  font-size: 28px;
  font-family: Rubik;
  margin: 0px;
  text-align: left;
}
.option_light .option__text {
  color: var(--dark-navy);
}
.option_dark .option__text {
  color: var(--pure-white);
}

.option__icon {
  margin-left: auto;
  height: 30px;
  width: 30px;
}
.option_selected {
  border: 3px solid var(--purple);
}
.option_selected .option__letter {
  background-color: var(--purple);
  color: var(--pure-white);
}
.option_correct {
  border: 3px solid var(--green);
}
.option_correct .option__letter {
  background-color: var(--green);
  color: var(--pure-white);
}
.option_incorrect {
  border: 3px solid var(--red);
}
.option_incorrect .option__letter {
  background-color: var(--red);
  color: var(--pure-white);
}
@media (max-width: 768px) {
  .option {
    padding: 12px;
    margin-bottom: 12px;
    border-radius: 12px;
  }
  .option__text {
    font-size: 18px;
  }
  .option__letter {
    min-width: 40px;
    height: 40px;
    font-size: 18px;
    margin-right: 16px;
  }
  .option__icon {
    width: 24px;
    height: 24px;
  }
}
</style>
