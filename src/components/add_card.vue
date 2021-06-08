<template>
  <section class="add_cards">
    <input
      class="add_cards__text"
      type="text"
      v-model="text"
      @keypress.enter="!isEmptyText ? add() : null"
    />
    <button :disabled="isEmptyText" @click="add()">Добавить</button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      text: "",
    };
  },
  computed: {
    isEmptyText() {
      return this.text.length === 0;
    },
  },
  methods: {
    add() {
      this.$emit("add", this.text);
    },
  },
};
</script>

<style lang="scss" scoped>
.add_cards {
  margin-bottom: 10px;

  &__text {
    margin-right: 10px;

    border: 0;
    border-radius: 6px;

    &:focus,
    &:focus-visible,
    &:valid {
      border: 0;
    }
  }
}
</style>