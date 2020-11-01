<!-- this is the parent -->

<template>
    <div id="app">
        <h1>Would you rather?</h1>

        <!-- if you want to see components on the webpage, reference them here -->
        <would-you-rather-question v-for="question in questions"
                                   v-bind:question="question.question"
                                   v-bind:answer1="question.answer1"
                                   v-bind:answer2="question.answer2"
                                   v-on:answer-changed="answerChanged">     <!-- from choiceMade() of child component -->
        </would-you-rather-question>

        <h1>You would rather...</h1>
        <span v-if="userChoice === ''">... ? Try making a selection above</span>

        <li v-show="userChoice != ''">{{ userChoice }}</li>
    </div>
</template>

<script>
    import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

    export default {
        name: 'App',
        components: {
            WouldYouRatherQuestion
        },
        data() {
            return {
                questions: [
                    {
                        id: 0,
                        question: '... be able to read minds or see one day into the future?',
                        answer1: 'Read minds',
                        answer2: 'See one day into the future',
                        // userSelectionMessage: ''
                    },
                    {
                        id: 1,
                        question: "... have an eagle's sight or an elephant's brain?",
                        answer1: "Eagle's sight",
                        answer2: "Elephant's brain",
                        // userSelectionMessage: ''
                    },
                    {
                        id: 2,
                        question: '... go back in the past and rectify a mistake or travel any where in the universe at the snap of your finger and never return?',
                        answer1: 'Go back in the past and rectify a mistake',
                        answer2: 'Travel any where in the universe at the snap of your finger and never return',
                        // userSelectionMessage: ''
                    }
                ],
                userChoice: ''
                // userChoice: []
            }
        },
        methods: {
            answerChanged(choice) {
                this.userChoice = `${choice}`
                // this.userChoice.push(choice);
            }
        }
    }
</script>

<style>
    body { background: aliceblue; }

    #app
    {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: yellowgreen;
        margin: 60px;
        background-color: #2c3e50;
        padding: 15px;
    }

    li
    {
        list-style-type: square;
        font-style: italic;
        font-weight: bold;
    }
</style>
