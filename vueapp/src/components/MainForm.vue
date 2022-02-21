<template>
    <v-container>
        <!-- use this piece to take in an input from the user, once the put in an input, show a good looking form that generates the number the user requests -->
        <label>How many participants? </label>
        <vue-numeric-input v-model="count" :min="3" :max="50" :isinput="false"></vue-numeric-input>
        <p>Count: {{ count }}</p>
        <ParticipantForm/>
        <v-modal v-if="valid">
            <SantaSetup :value="participantData" />
        </v-modal>
    </v-container>
</template>

<script>
import ParticipantForm from './ParticipantForm.vue';
import SantaSetup from './SantaSetup.vue';

export default {
    data() {
        return {
            //you will need to set this up, it should take in an input in html from the user
            //to get the total count, you will use this count to generate the form with a v-data-table or some sort of thing
            //to create the full form, use vuetify!
            count: 3,
            inputRule: 'change this to where the input gets validated, it must be between 3 and 50! look into this on vue',
            valid: 'this will be a boolean that will return true if the input is correct, on this SHOW the new form with each participant, so use a v-if',
            //this will be an object bound to the table/form created to pass in to the santaSetup, they shoudl be validated from the participant form
            //this will be filled dynamically
            participantData: [{ name: '', email: '', about: '' }]
        }
    },
    components: {
      ParticipantForm, SantaSetup
    },
    methods: {
        submit(){
            //this can be wehre you validate on submission or on form button click to generate full form,
            //this will pass the data placed into the participant data object into the santaSetup modal, pass it as a prop, you won't need to show the modal, unless you decide to, but the modal
            //itself will be a "Generating..." while the algorithm happens behinds the scenes

        },
        add(){
            //another method you could use to add each form to your participant data object by pushing it, you are pushing an object to an array
        }
    }
}
</script>
