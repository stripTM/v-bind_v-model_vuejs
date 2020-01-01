<template>
  <div id="app">
    <fieldset>
      <legend>Parent editor primitive</legend>
      <label>text:
        <input type="searchText" v-model="searchText">
      </label>
    </fieldset>
    <ChildComponentPrimitive v-model="searchText" v-bind:text="searchText"/>
    <hr/>
    <fieldset>
      <legend>Parent editor object</legend>
      <label>href:
        <input type="text" v-model="link.href">
      </label>
      <label>desc:
        <input type="text" v-model="link.desc">
      </label>
    </fieldset>
    <ChildComponentObject v-model="link" v-bind:link="link"/>
  </div>
</template>

<script>
import ChildComponentPrimitive from "./components/ChildComponentPrimitive"
import ChildComponentObject from "./components/ChildComponentObject";

export default {
  name: "App",
  components: {
    ChildComponentPrimitive,
    ChildComponentObject
  },
  data() {
    return {
      searchText: "",
      link: { href: "#", desc: "ss" }
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.child {
  margin-left: 1rem;
}
</style>
