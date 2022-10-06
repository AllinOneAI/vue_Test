<script>
  function sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
  }
  export default {
    
    data() {
      return {
        count: 1,
        toData: null,
      }
    },

    methods: {

      increment() {
        this.count++
      },

      decrement() {
        if(this.count > 1) {
          this.count--
        }
      },

      async fetcher() {
        this.toData = null
        const res = await fetch(`https://jsonplaceholder.typicode.com/todos/${this.count}`)
        this.toData = await res.json()
      }
    },

    mounted() {
      this.fetcher();
    },

    watch: {
      count() {
        this.fetcher();
      }
    }

  }
</script>

<template>
  <h1 ref="h">ZDAROVA</h1>
  <p>Todo ID: {{ count }}</p>
  <button @click="increment">Fetch next todo</button>
  <button @click="decrement">Fetch previous todo</button>
  <p v-if="!toData">Loading...</p>
  <p v-else>{{ toData }}</p>
</template>

<style>

</style>