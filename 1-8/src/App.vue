<script>
  let id = 0;
  export default {
    data(){
      return {
        divs: "div",
        inputs: "input",
        knopkas: "knopka",
        counter: 0,
        text: '',
        dinisText: '',
        status: true,
        dinises: [],
        hideCompleted: false,
      }
    },
    methods: {
      increment () {
        this.status = !this.status;
        this.counter++
      },

      addDinis () {
        this.dinises.push({id: id++, text: this.dinisText, is: false});
        this.dinisText='';
      },

      rmDinis (dinis) {
        this.dinises = this.dinises.filter((t) => t !== dinis)
      }

    },
    computed: {
        filteredDinises() {
          return this.hideCompleted ? this.dinises.filter((t) => !t.is) : this.dinises;
        }
    }
  }
</script>

<template>
  <div :class="divs">
    <button :class="knopkas" @click="increment">{{ counter }}</button>
    <input :class="inputs" v-model="text">
    <p v-if="status">{{ text }}</p>
    <p v-else>{{ text.split("").reverse().join("") }}</p>
  </div>

  <br>

  <div :class="divs">
    <input :class="inputs" v-model="dinisText">
    <button :class="knopkas" @click="addDinis">Add Checked Dinis</button>
    <ol type="I">
      <li v-for="dinis in filteredDinises" :key="dinis.id">
        <input type="checkbox" v-model="dinis.is">
        <span :class="{ is: dinis.is }">{{dinis.text}}</span>
        <button class="rmKnopka" @click="rmDinis(dinis)">X</button> 
      </li>
    </ol>
    <button :class="knopkas" @click="hideCompleted = !hideCompleted">
      {{  hideCompleted ? "Show all" : "Hide completed"  }}
    </button>
  </div>
</template>

<style> 
  .is {
    text-decoration: line-through;
  }

  .rmKnopka{
    color: rebeccapurple;
    background-color: aqua;
    width: 30px;
    height: 30px;
  }

  .div {
    padding: 30px;
    border-width: 3px;
    border-color: black;
    border-style: groove;
  }

  .input {
    width: 30%;
    height: 25px;
  }
  
  .knopka {
    border-radius: 10px;
    width: 130px;
    height: 30px;
    background-color: rebeccapurple;
    color: aqua;
  }

</style>
