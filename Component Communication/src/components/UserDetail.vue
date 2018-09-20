<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ myName }}</p>
        <p>User Age: {{ userAge }}</p>
        <p>Switched Name: {{ switchName() }}</p>
        <p>User City: {{ userCity }}</p>
        <button @click="resetName">Reset Name</button>
        <button @click="resetFn">Reset Name With Callback</button>
    </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  props: {
    //   'myName': String,
    myName: {
        type: String,
        required: true
        //default: 'Huppeldepup'//Doesn't make sence with a required (since it would be filled anyway)
    },
    resetFn: Function,
    userAge: Number,
    userCity: String,
  }, 
  methods: {
    switchName() {
        return this.myName.split('').reverse().join('');
    },
    resetName() {
        this.myName = 'Joris';
        this.$emit('nameWasReset', this.myName);
    },
  },
  created() {
      eventBus.$on('ageWasEdited', (data) => {
          this.userAge = data;
      });
  }
};
</script>

<style scoped>
div {
  background-color: lightcoral;
}
</style>