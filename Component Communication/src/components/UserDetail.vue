<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ myName }}</p>
        <p>Switched Name: {{ switchName() }}</p>
        <button @click="resetName">Reset Name</button>
    </div>
</template>

<script>
export default {
  props: {
    //   'myName': String,
    myName: {
        type: String,
        required: true
        //default: 'Huppeldepup'//Doesn't make sence with a required (since it would be filled anyway)
    }
  }, 
  methods: {
    switchName() {
        return this.myName.split('').reverse().join('');
    },
    resetName() {
        this.myName = 'Joris';
        this.$emit('nameWasReset', this.myName);
    },
  }
};
</script>

<style scoped>
div {
  background-color: lightcoral;
}
</style>