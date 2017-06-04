<template>
  <div class="component">
    <h3>You may edit the User here</h3>
    <p>Edit me!</p>
    <p>User Age: {{ agePassedIn }}</p>
    <button @click="editAge">Edit Age</button>
  </div>
</template>

<script>
  import { eventBus } from '../main';
  export default {
    props: ['userAge'],
    data() {
      return {
        agePassedIn: this.userAge
      }
    },
    methods: {
      editAge() {
        this.agePassedIn = 30;
        // this.$emit('ageWasEdited', this.userAge);
        // eventBus.$emit('ageWasEdited', this.agePassedIn);
        eventBus.changeAge(this.agePassedIn);
      }
    }
  }
</script>

<style scoped>
  div {
    background-color: lightgreen;
  }
</style>
