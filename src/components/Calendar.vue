<template>
  <!-- CSS only -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-giJF6kkoqNQ00vy+HMDP7azOuL0xtbfIcaT9wjKHr8RbDVddVHyTfAAsrekwKmP1" crossorigin="anonymous">
  <h1>Vue calendar</h1>
  <section>
    <h4 class="pr">{{ currentMonthName }} {{ currentYear }}</h4>
  </section>
  <section class="wrapper">
    <p v-for="day in days" :key="day" class="wrapper-inner">{{ day }}</p>
  </section>
  <section class="wrapper">
    <p class="wrapper-inner" v-for="num in startDay()" :key="num"></p>
<!--  TODO: Добавить проверку на текущий месяц и год что-бы дата выводилась только в этом месяце  -->
<!--    { current: num == currentDate}-->
    <p class="wrapper-inner" v-for="num in daysInMonth()" :key="num" :class="currentDateClass(num)">{{ num }}</p>
  </section>
  <section style="width: 400px; margin: 0 auto; display: flex; justify-content: space-between">
    <button type="button" class="btn btn-outline-primary" @click="prev()">Предыдущий</button>
    <button type="button" class="btn btn-outline-primary" @click="next()">Следующий</button>
  </section>
</template>

<script>
export default {
  name: "Calendar",
  data() {
    return {
      currentDate: new Date().getUTCDate() + 1,
      currentMonth: new Date().getMonth() + 1,               // Цифра
      currentYear: new Date().getFullYear(),
      // currentDate: new Date(this.currentYear, this.currentMonth).getUTCDate(),
      days: ['Вс', 'Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб']
    }
  },
  methods: {
    daysInMonth() {
      return new Date(this.currentYear, this.currentMonth, 0).getDate()
    },
    startDay() {
      return new Date(this.currentYear, this.currentMonth - 1).getDay()
    },
    next() {
      if (this.currentMonth === 12) {
        this.currentMonth = 1
        this.currentYear++
      } else {
        this.currentMonth++;
      }
    },
    prev() {
      if (this.currentMonth === 1) {
        this.currentMonth = 12
        this.currentYear--
      } else {
        this.currentMonth--;
      }
    },
    currentDateClass(num) {
      const calenderFullDate = new Date(
          this.currentYear,
          this.currentMonth - 1,
          num
      ).toDateString()
      const currentFullDate  =  new Date().toDateString()
      console.log(calenderFullDate)
      console.log(currentFullDate)
      return calenderFullDate === currentFullDate ? 'current' : ''
    }
  },
  computed: {
    currentMonthName() {
      return new Date(
          this.currentYear,
          this.currentMonth - 1
      ).toLocaleString('default',{ month: 'long' })
    }
  }
}
</script>

<style scoped>
  .wrapper {
    margin: 0 auto;
    display: flex;
    width: 350px;
    flex-wrap: wrap;
    justify-content: start;
  }

  .wrapper-inner {
    width: 50px;
    /*flex-grow: 1;*/
  }

  .p {
    padding: 5px;
  }

  .pr {
    padding-right: 40px;
  }

  .current {
    background-color: #ffd2e8;
    border-radius: 10%;
  }

  p:hover {
    background-color: #9fcfff;
    border-radius: 10%;
  }
</style>