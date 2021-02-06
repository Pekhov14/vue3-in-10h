<template>
  <h1>Markdown App</h1>
  <section class="flex">
    <article class="box">
<!--      v-model.lazy-->
      <textarea class="full" :value="text" @input="update"></textarea>
    </article>
    <article class="box rg" v-html="markedText"></article>
  </section>
</template>

<script>
import marked from "marked"
import debounce from "../utilities/mixins/debounce"

export default {
  name: "Markdown",
  mixins: [debounce],
  data() {
    return {
      text: "",
    }
  },
  computed: {
    markedText() {
      return marked(this.text)
    }
  },
  methods: {
    update(e) {
      const task = () => this.text = e.target.value
      this.debounce(task, 500)
    }
  }
}
</script>

<style scoped>
  .flex {
    display: flex;
    width: 100%;
    /*background: blue;*/
  }

  .box {
    flex: 1 0 340px;
    max-width: 50%;
    border-left: 1px solid #c4c4c4;
  }

  .rg {
    /*height: calc(100vh - 18.5px);*/
    height: 79.5vh;
    background: #efefef;
    text-align: start;
    padding: 10px;
  }

  .full {
    width: 100%;
    height: 100%;
  }
</style>