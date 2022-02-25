<template>
  <v-container>
    <v-card>
      <v-card-title>Generating Secret Santas!</v-card-title>
      <v-progress-circular
        v-if="randomizing"
        color="red"
        indeterminate
        size="64"
      />
      <v-card-subtitle v-else>Secret Santas generated.</v-card-subtitle>
    </v-card>
    <div v-if="generated">
      <EmailModal :value="emailObject" />
    </div>
  </v-container>
</template>
<script>
import EmailModal from "./EmailModal.vue";

export default {
  props: ["value"],
  components: {
    EmailModal,
  },
  data() {
    return {
      //i will generate list of each email and generate them randomly in the methods, set up generated to true if
      //randomize is complete with checks to make sure everyone has someone
      generated: false,
      randomizing: true,
      timerCount: 10,
      emailObj: {
        to_name: '',
        to_email: '',
        general_message: '',
        assigned_name: '',
        assigned_details: ''
      },
    };
  },
  methods: {
    randomize() {
      //i will mess around with this and make it work
      //will make email object either loop hrough each email modal in a v-for for each in the data object
      //do a full objec twith everytwo and from, going through one will be easier to debug probably
      setTimeout(() => {
        this.randomizing = !this.randomizing;
      }, 3000);
      if (this.generated) {
        this.randomizing = false;
      }
      this.fix();
    },
    fix() {
      console.log("emmiting now");
      //this is when email modal failed, it will return the error message to here as well so i can fix it
      //when it is fixed, will need to recall email modal to try again
    },
  },
  mounted() {
    console.log(this.value);
    this.randomize();
  },
};
</script>
