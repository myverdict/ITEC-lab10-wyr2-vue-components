<!-- this is the child component of the App.vue -->

<template>
    <div class="wyr">
        <h2>Would you rather...</h2>
        <h3>{{ question }}</h3>

        <!-- creating radio buttons for the answers -->
        <input type="radio"
               v-model="choice"
               v-bind:value="answer1"
               v-on:change="choiceMade">
        <label>{{ answer1 }}</label>

        <input type="radio"
               v-model="choice"
               v-bind:value="answer2"
               v-on:change="choiceMade">
        <label>{{ answer2 }}</label>
    </div>
</template>

<script>
    export default {
        name: 'WouldYouRatherQuestion',
        // never modify a prop in a component
        props: {
            question: String,
            answer1: String,
            answer2: String,
        },
        // collect this data & this data is sent to the parent App.vue
        data() {
            return {
                choice: ''          // initially no choice made
            }
        },
        methods: {
            choiceMade() {
                // send an event to the parent App.vue about the choice made
                this.$emit('answer-changed', this.choice)
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 { margin: 40px 0 0; padding-bottom: 15px; }

    .wyr
    {
        border: 2px yellow solid;
        background: burlywood;
        color: indigo;
        margin: 20px;
        padding: 15px;
        text-align: left;
    }

    label { padding-right: 15px; }
</style>
