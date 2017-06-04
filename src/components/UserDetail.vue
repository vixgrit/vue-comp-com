<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <p>User name: {{ switchName() }}</p>
    <p>User Age: {{ agePassedIn }}</p>
    <button @click="resetName">Reset Name</button>
    <button @click="resetFn()">Reset Name</button>
  </div>
</template>

<script>
  import { eventBus } from '../main';
  export default {
    props: {
      myName: {
        type: String,
        default: 'Max'
      },
      resetFn: Function,
      userAge: Number
    },
    data() {
      return {
        agePassedIn: this.userAge
      }
    },
    methods: {
      switchName() {
        return this.myName.split('').reverse().join('');
      },
      resetName() {
        this.$emit('nameWasReset', 'Max');
      }
    },
    created() {
      eventBus.$on('ageWasEdited', (age) => {
        this.agePassedIn = age;
      })
    }
  }
</script>

<style scoped>
  div {
    background-color: lightcoral;
  }
</style>
