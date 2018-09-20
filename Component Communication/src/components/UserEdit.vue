<template>
    <div class="component">
        <h3>You may edit the User here</h3>
        <p>Edit me!</p>
        <p>User Age: {{ userAge }}</p>
        <p>User City: {{ userCity }}</p>
        <button @click="editAge">Edit Age</button>
        <button @click="editCityFn">Edit City</button>
    </div>
</template>

<script>
    export default {
        props: ['userAge', 'userCity', 'editCityFn'],
        methods: {
            editAge() {
                this.userAge = '22';
                this.$emit('ageWasEdited', this.userAge);
            },
        }
    }
</script>

<style scoped>
    div {
        background-color: lightgreen;
    }
</style>
