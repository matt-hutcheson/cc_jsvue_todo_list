<template>
  <div id="app">
    <h1>ToDo's</h1>
    <form v-on:submit.prevent="newToDo">
      <input type="text" id="new-item" required v-model="newItem">
      <label for="high">High</label>
      <input type="radio" value="high" name="importance" id="high" v-model="radioButtonValue">
      <label for="low">Low</label>
      <input type="radio" value="low" name="importance" id="low" v-model="radioButtonValue" checked>
      <input type="submit" value="Save Item">
    </form>
    <ul >
      <li v-for="(item, index) in items" v-bind:key="index">
        {{item.name}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {name: "Buy shopping", important: false},
        {name: "Clean bathroom", important: true},
        {name: "Car's MOT", important: false}
        ],
      newItem: "",
      radioButtonValue: "low"
    }
  },
  methods: {
    newToDo: function () {
      this.items.push(
        {name: this.newItem, important: (this.radioButtonValue === 'high' ? true: false)}
      );
      this.newItem = "";
    }
  }
}
</script>

<style>

</style>
