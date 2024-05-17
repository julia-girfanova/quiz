<template>
  <div v-if="logo === null" class="new-quiz-logo">
    <button @click="open_file" class="new-quiz-logo__button">
      <img class="new-quiz-logo__plus" src="/plus.svg" />
    </button>
    <input
      @change="select_logo"
      ref="logo_input"
      class="new-quiz-logo__input"
      type="file"
    />
  </div>
  <div v-if="logo !== null" class="new-quiz-logo__preview">
    <div @click="delete_logo" class="new-quiz-logo__overlay">
      <img src="/icon-close.svg" />
    </div>
    <img class="new-quiz-logo__image" :src="logo_url" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      logo: null,
    };
  },
  methods: {
    open_file() {
      this.$refs["logo_input"].click();
    },
    select_logo($event) {
      const selected_logo = $event.target.files[0];
      if (selected_logo) {
        this.logo = selected_logo;
      }
    },
    delete_logo() {
      this.logo = null;
    },
  },
  computed: {
    logo_url() {
      if (this.logo !== null) {
        return URL.createObjectURL(this.logo);
      }
      return "";
    },
  },
};
</script>

<style>
.new-quiz-logo {
  position: relative;
}
.new-quiz-logo__button {
  width: 56px;
  height: 56px;
  border-radius: 8px;
  background-color: var(--pure-white);
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  border: none;
}
.new-quiz-logo__plus {
  width: 30px;
  height: 30px;
}
.new-quiz-logo__input {
  opacity: 0;
  width: 0px;
  height: 0px;
  position: absolute;
}
.new-quiz-logo__image {
  width: 100%;
  height: 100%;
}
.new-quiz-logo__preview {
  width: 56px;
  height: 56px;
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
}
.new-quiz-logo__preview:hover .new-quiz-logo__overlay {
  opacity: 0.9;
  transition: 0.3s;
}
.new-quiz-logo__overlay {
  width: 100%;
  height: 100%;
  position: absolute;
  opacity: 0;
  background-color: var(--dark-navy);
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
