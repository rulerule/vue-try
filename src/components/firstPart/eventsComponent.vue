<template>
  <div class="second-component">
    <button v-on:click="increase(2, $event)">Click me </button>
    <button v-on:click="counter++">Click me </button>
    <p>{{ counter }}</p>
    <p v-on:mousemove="updateCoordinates">
      Coordinates: {{x}} / {{y}}
      <span v-on:mousemove.stop="">DEAD SPOT</span>
    </p>
    <input type="text" v-on:keyup.enter="alertMe">
  </div>
</template>

<script>
export default {
  data () {
    return {
      counter: 0,
      x: 0,
      y: 0
    }
  },
  methods: {
    increase: function (amount, event) {
      this.counter += amount
    },
    updateCoordinates: function (event) {
      this.x = event.clientX
      this.y = event.clientY
    },
    alertMe: function () {
      alert('Alert')
    }
  }
}
</script>

<style>
</style>
