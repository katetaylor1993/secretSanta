<template>
  <v-container>
    <!-- use this piece to take in an input from the user, once the put in an input, show a good looking form that generates the number the user requests -->
    <v-card-title>Participant Forms</v-card-title>
    <v-card-subtitle>
      Please enter each participant's name, email, and a short description of
      them below:
    </v-card-subtitle>
    <ParticipantForm />
    <div v-if="valid">
      <SantaSetup @failure="error" :value="participantData" />
    </div>
    <div v-if="problem">
      <ErrorPopUpModal />
    </div>
  </v-container>
</template>

<script>
import ParticipantForm from "./ParticipantForm.vue";
import SantaSetup from "./SantaSetUpModal.vue";
import ErrorPopUpModal from "./PopUpModal.vue";

export default {
  data() {
    return {
      //you will need to set this up, it should take in an input in html from the user
      //to get the total count, you will use this count to generate the form with a v-data-table or some sort of thing
      //to create the full form, use vuetify!
      count: 0,
      inputRule:
        "change this to where the input gets validated, it must be between 3 and 50! look into this on vue",
      valid: true, //this will be an object bound to the table/form created to pass in to the santaSetup, they shoudl be validated from the participant form
      //this will be filled dynamically
      participantData: [{ name: "", email: "", about: "" }],
      problem: false,
    };
  },
  components: {
    ParticipantForm,
    SantaSetup,
    ErrorPopUpModal,
  },
  methods: {
    submit() {
      //this can be wehre you validate on submission or on form button click to generate full form,
      //this will pass the data placed into the participant data object into the santaSetup modal, pass it as a prop, you won't need to show the modal, unless you decide to, but the modal
      //itself will be a "Generating..." while the algorithm happens behinds the scenes
    },
    add() {
      //another method you could use to add each form to your participant data object by pushing it, you are pushing an object to an array
    },
    error() {
      console.log("in error");
      this.problem = true;
    },
  },
};
</script>
