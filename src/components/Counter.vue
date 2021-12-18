<template>
  <h1>{{ customTitle }}</h1>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

  <div>
    <button @click="increase">+1</button>
    <button @click="decrease">-1</button>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    start: {
      type: Number,
      default: 100,
      // required: true,
      validator(value) {
        return value >= 0;
      },
    },
  },
  name: "Counter",
  data() {
    return {
      counter: this.start,
    };
  },
  methods: {
    increase() {
      this.counter++;
    },
    decrease() {
      this.counter--;
    },
  },
  computed: {
    squareCounter() {
      console.log("computed square counter");
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title || "Counter";
    },
  },
};
</script>

<style>
button {
  background-color: #6e3cbc;
  border-radius: 5px;
  border: none;
  color: white;
  cursor: pointer;
  margin: 0 5px;
  padding: 10px 15px;
}
</style>