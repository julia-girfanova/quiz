<template>
  <div class="theme-switcher">
    <img class="theme-switcher__icon" :src="`/icon-sun-${theme}.svg`" />
    <label class="theme-switcher__checkbox">
      <input
        class="theme-switcher__input"
        type="checkbox"
        :checked="checked"
        @change="change_theme"
      />
      <span class="theme-switcher__slider"></span>
    </label>
    <img class="theme-switcher__icon" :src="`/icon-moon-${theme}.svg`" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      checked: false,
    };
  },
  computed: {
    theme() {
      if (this.checked === true) {
        return "dark";
      } else {
        return "light";
      }
    },
  },
  methods: {
    change_theme() {
      if (this.checked === true) {
        this.checked = false;
      } else {
        this.checked = true;
      }
      this.$emit("theme-changed", this.theme);
    },
  },
};
</script>

<style>
.theme-switcher {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.theme-switcher__checkbox {
  margin: 0px 16px;
  background-color: var(--purple);
  height: 28px;
  width: 48px;
  border-radius: 99px;
  cursor: pointer;
  align-items: center;
  box-sizing: border-box;
  position: relative;
}
.theme-switcher__icon {
  width: 24px;
  height: 24px;
}
.theme-switcher__input {
  appearance: none;
  -webkit-appearance: none;
  position: absolute;
  opacity: 0;
}
.theme-switcher__slider {
  background-color: var(--pure-white);
  width: 20px;
  height: 20px;
  border-radius: 90%;
  display: inline-block;
  position: absolute;
  top: 4px;
  left: 4px;
  transition: 0.2s;
}
.theme-switcher__input:checked ~ .theme-switcher__slider {
  left: 24px;
}
@media (max-width: 768px) {
  .theme-switcher__checkbox {
    height: 20px;
    width: 32px;
    margin: 0px 8px;
  }
  .theme-switcher__slider {
    height: 12px;
    width: 12px;
  }
  .theme-switcher__icon {
    width: 16px;
    height: 16px;
  }
  .theme-switcher__input:checked ~ .theme-switcher__slider {
    left: 16px;
  }
}
</style>
