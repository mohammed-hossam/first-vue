<template>
  <div class="hello">
    <p>{{ fullName }}</p>
    <!-- <input type="number" v-model="number1" /> -->
    <!-- or -->
    <input type="number" v-bind:value="number1" @input="setStateNumber1" />
    <input type="number" v-model="number2" />

    <button type="button" v-on:click="add">Add</button>
    <br />

    <button type="button" v-on:click="welcome('hy how are you', $event)">
      log to concole wlecome msg
    </button>
    <br />

    <label for="modify">events modifiers(key modifiers)</label>
    <input id="modify" type="text" @keyup.enter="handleInput" />
    <p>{{ inputEventModifiers }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      firstName: 'Mohammed',
      secondName: 'hossam',
      number1: 0,
      number2: 0,
      inputEventModifiers: '',
    };
  },
  methods: {
    add() {
      console.log(typeof this.number1);
      console.log(this.number1 + this.number2);
    },
    setStateNumber1(e) {
      this.number1 = +e.target.value;
    },
    welcome(msg, e) {
      console.log(msg);
      console.log(e);
    },
    handleInput(e) {
      this.inputEventModifiers = e.target.value;
    },
  },
  computed: {
    fullName() {
      console.log('compted full name gets called');
      return `${this.firstName} ${this.secondName.toUpperCase()}`;
    },
  },
  watch: {
    number1() {
      setTimeout(() => {
        console.log(this.number1);
      }, 3000);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
