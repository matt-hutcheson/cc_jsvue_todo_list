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
      <li v-for="(item, index) in items" v-bind:key="index" v-bind:class="item.important ? 'priority': 'not-priority'">
        <span>
          {{item.name}}
        </span>
        <span v-if="item.important">
          High Priority!
        </span>
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
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-between;
}

li.not-priority {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.priority {
  border: 2px solid #f2360c;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

input[type="submit"]{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>
