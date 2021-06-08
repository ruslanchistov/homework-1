<template>
  <div class="card">
    <h3>{{ text }}</h3>

    <button @click="remove" class="card__delete point">X</button>
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: "Пусто",
    },
  },
  methods: {
    remove() {
      //Генерируем событие remove на уровень выше и передаем индекс элемента в массиве, чтобы его потом удалить
      this.$emit("remove", this.index);
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  height: 100px;
  width: 200px;
  background: blueviolet;
  margin: 5px;
  border-radius: 10px;
  border: 2px solid black;
  color: black;
  position: relative;

  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  &__delete {
    position: absolute;
    top: 3px;
    right: 3px;

    color: white;
    background: transparent;
    border: none !important;
  }
}
</style>