<template>
  <div class="home">
    <calculator></calculator>
    <Time></Time>

    <section>
      
      <add-card @add="onAdd"></add-card>
      <card_list :cards="cards" @remove="onRemove"></card_list>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import Calculator from "../components/calculator";
import Time from "../components/time";
import card_list from "../components/card_list";
import AddCard from "../components/add_card";
// класс создания элемента
class card_ {
  constructor(text) {
    this.text = text;
  }
}
// класс обращения к кэшу
class Cache {
  get_card() {
    const card_from_cache = localStorage.getItem("cards");
    // Проверяем не пустой ли кэш, если пустой, то возвращаем пустой массив,
    //  если не пустой, то превращаем его из строки в JS формат.
    return card_from_cache ? JSON.parse(card_from_cache) : [];
  }
  set_card(cards) {
    localStorage.setItem("cards", JSON.stringify(cards));
  }
}

export default {
  name: "Home",
  components: {
    Calculator,
    Time,
    card_list,
    AddCard,
  },
  data() {
    return {
      cards: [],
    };
  },
  methods: {
    //Добавляем задачу с определенным текстом
    onAdd(text) {
      //Создаем класс для работы с кэшем
      const card_Cache = new Cache();
      //Достаем заачи из кэша
      const cache_card = card_Cache.get_card();

      //Создаем новую задачу
      const new_card = new card_(text);
      //Добавляем в текущие задачи на странице
      this.cards.push(new_card);
      //Добавляем в кэш
      cache_card.push(new_card);

      //Сохраняем задачи в кэше
      card_Cache.set_card(cache_card);
    },
    //Удаляет задачу по индексу
    onRemove(index) {
      //Создаем класс для работы с кэшем
      const card_Cache = new Cache();
      //Достаем заачи из кэша
      let cache_card = card_Cache.get_card();

      //Удаляем один элемент из массива по определенному индексу (см функцию splice)
      this.cards.splice(index, 1);
      cache_card.splice(index, 1);

      //Сохраняем задачи в кэше
      card_Cache.set_card(cache_card);
    },
  },
  //Вызывается когда компонент монтируется на html страницу
  mounted() {
    //Создаем класс для работы с кэшем
    const card_Cache = new Cache();
    //Достаем заачи из кэша
    const card_from_cache = card_Cache.get_card();
    //Присваиваем массиву задач в компоненте значение из кэша, из-за того что значения в компоненте поменялось, задачи поменются в html
    this.cards = card_from_cache;
  },
};
</script>
<style>
.point{
   list-style-type: none;
  cursor: pointer;
}
</style>
