<script>
export default {
  data() {
    return {
      count: 0
    }
  },

  methods: {
    increment() {
      this.count++
    }
  },

  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>

<template>
  <div>
    <button @click="increment" class="like">Like - {{ count }}</button>
  </div>
</template>
