<template>
  <h1 class="text-center">dcHeros {{ herosCount }}</h1>
  <p>{{ fullname }}</p>
  <ul>
    <li v-for="(hero, index) in dcHeros" :key="hero.name">
      <span>{{ hero.name }} <button v-on:click="removeHero(index)">x</button></span>
      <input type="text">
    </li>
  </ul>
  <!-- v-model ДИРЕКТИВЫ -->
  <!-- модификаторы
   trim - обрезат пробелы
   lazy - изменяет переменную после un фокуса
   -->
  <form @submit.prevent="addHero">
    <input v-model.lazy.trim="newHero"> <!-- [attribute] -->
    <button type="submit">Add Hero</button> <!-- :disabled="isDisabled" @click="alert('hee')" -->
  </form>
</template>

<script>
export default {
  name: "DcHeros",
  data() {
    return {
      title: "Dc Heros",
      isDisabled: true,
      newHero: "Aquaman))",
      dcHeros: [
        {
          name: "SuperGirl"
        },
        {
          name: "Arrow",
        },
        {
          name: "Batman"
        },
        {
          name: "Superman"
        }
      ]
    }
  },
  // computed свойства для счета (кэшириються)
  computed: {
    herosCount() {
      return this.dcHeros.length
    },
    randC() {
      return Math.random()
    },
    fullname: {
      get() {
        return `Full name is ${this.fname} ${this.lname}`;
      },
      set(fullname) {
        alert(fullname);
      }
    }
  },
  methods: {
    addHero() {
      if (this.newHero !== '') {
        this.dcHeros.push({name: this.newHero})
        this.newHero = ''
      }
    },
    removeHero(index) {
      this.dcHeros = this.dcHeros.filter((hero, i) => i !== index)
    },
    randM() {
      return Math.random()
    },
    setFullName() {
      this.fullname = 'Test))'
    }
  },
}
</script>

<style scoped>

</style>