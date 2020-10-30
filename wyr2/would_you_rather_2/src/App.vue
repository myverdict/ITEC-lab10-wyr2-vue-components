<!-- this is the parent -->

<template>
    <div id="app">
        <h1>Would you rather...</h1>

        <!-- if you want to see components on the webpage, reference them here -->
        <would-you-rather v-bind:question="wyrQuestion"
                          v-bind:answer1="wyrAnswer1"
                          v-bind:answer2="wyrAnswer2"
                          v-on:answer-changed="answerChanged">
        </would-you-rather>

        <p>{{ userSelectionMessage }}</p>
    </div>
</template>

<script>
    import WouldYouRather from './components/WouldYouRather.vue'

    export default {
        name: 'App',
        components: {
            WouldYouRather
        },
        data() {
            return {
                wyrQuestion: 'Would you rather be able to read minds or see one day into the future?',
                wyrAnswer1: 'Read minds',
                wyrAnswer2: 'See one day into the future',
                userSelectionMessage: ''
            }
        },
        methods: {
            answerChanged(choice) {
                this.userSelectionMessage = `Thank you! You chose, "${choice}".`
            }
        }
    }
</script>

<style>
    body { background: teal; }

    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: yellowgreen;
        margin-top: 60px;
        background-color: #2c3e50;
        padding: 15px;
    }
</style>
