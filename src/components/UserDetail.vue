<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <p>User name: {{ switchName() }}</p>
    <button @click="resetName">Reset Name</button>
  </div>
</template>

<script>
  export default {
    props: {
      myName: {
        type: String,
        default: 'Max'
      }
    },
    methods: {
      switchName() {
        return this.nameProxy().split('').reverse().join('');
      },
      resetName() {
        this.$emit('nameWasReset', 'Max');
      },
      nameProxy() {
        return this.myName;
      }
    }
  }
</script>

<style scoped>
  div {
    background-color: lightcoral;
  }
</style>
