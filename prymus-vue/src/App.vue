<template>
  <div>
    <h1>My vue</h1>
    <p>Example paragraph :)</p>
    <img src="https://picsum.photos/200/300/?random">
    <div>
      {{name}} {{surname}} {{age}}
    </div>
    <span v-bind:title="alert">This is span 1</span>
    <br>
    <span :title="alert">This is span 2</span>
    <br>
    <div> {{age}}</div>
    <input type="text"  v-model="age">
    <br>
    <div v-if="age >= 18">Adult</div>
    <div v-else>Child</div>
    <ul id="v-for">
      <li v-for="fruit in fruits" :key="fruit">{{ fruit }}</li>
    </ul>
    <div> Clicked {{counter}} times! </div>
    <button @click="buttonClicked">Click!!</button>
    <button v-on:click="counter = 0">Start over</button>
  </div>
  
</template>

<script>
  export default {
    data: function () {
      return {
        name: 'Natalia',
        surname: 'Piękoś',
        age: 20,
        alert: 'This is alert',
        fruits: [ "Banana", "Apple", "Orange"],
        counter: 0,
      } 
    },

    methods: {
      buttonClicked: function () {
        this.counter = this.counter + 1; 
      }
    }
  };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
