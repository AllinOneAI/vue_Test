<script>
  import childComponent from "./components/childComponent.vue"
  export default {
    components: {
      childComponent
    },

    data() {
      return {
        message: "Dinis",
      }
    }
  }
</script>

<template>
  <childComponent @response="(msg) => message = msg">vse tam slyshno</childComponent>
  <h2>{{ message }}</h2>

</template>

<style>

</style>