<template>
  <div id="app">
    <Header />
    <input type="text" v-model="inputDataText" @input="inputText($event)" />
    {{fullData}}
    <ul>
      <li v-for="(item,index) of inputData" :key="index">{{item.name}} : {{item.age}}</li>
    </ul>
    <h3 v-for="(i, idx) of inputEventText" :key="idx">{{i}}</h3>
    <div class="content">
      <router-view />
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header";
export default {
  name: "App",
  components: { Header },
  data() {
    return {
      inputEventText: [],
      inputDataText: null,
      inputData: [
        { name: "test", age: 5 },
        { name: "test2", age: 7 },
        { name: "test3", age: 9 },
        { name: "test4", age: 15 },
      ],
    };
  },
  methods: {
    inputText(e) {
      this.inputEventText.push(e.target.value);
      console.log(e);
    },
  },
  computed: {
    fullData() {
      return `${this.inputData[0].name} - ${this.inputData[0].age}`;
    },
  },
  watch: {},
  create() {},
  mounted() {},
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
