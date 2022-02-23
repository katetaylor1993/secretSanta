<template>
  <v-container>
    <v-card light>
      <v-row justify="center">
        <v-card-title
          >Number of Participants:
          <input type="number" v-model="total" @input="validateTotal" />
          <v-btn color="red" :disabled="!enableBtn" @click="submit"
            >Submit</v-btn
          >
        </v-card-title>
      </v-row>
      <v-card dark v-if="displayForms">
        <v-col>
          <v-card-title style="font-size: 1.5rem; font-weight: 550"
            >Participant Forms:</v-card-title
          >
          <v-card-subtitle style="font-size: 1rem">
            Please enter each participant's name, email, and a short description
            of them below.
          </v-card-subtitle>
          <v-card-text v-for="index in parseInt(total)" :key="index">
            <ParticipantForm :index="index" @add="add" />
          </v-card-text>
          <v-row justify="center">
            <v-btn color="green" @click="generate">Generate</v-btn>
          </v-row>
        </v-col>
      </v-card>

      <div v-if="valid">
        <SantaSetup @failure="error" :value="participantData" />
      </div>
      <div v-if="problem">
        <ErrorPopUpModal />
      </div>
    </v-card>
  </v-container>
</template>

<script>
import ParticipantForm from "./ParticipantForm.vue";
import SantaSetup from "./SantaSetUpModal.vue";
import ErrorPopUpModal from "./ErrorPopUpModal.vue";

export default {
  data() {
    return {
      total: 0,
      valid: false, //this will be an object bound to the table/form created to pass in to the santaSetup, they shoudl be validated from the participant form
      //this will be filled dynamically
      participantData: [],
      problem: false,
      enableBtn: false,
      displayForms: false,
      counter: 0,
    };
  },
  components: {
    ParticipantForm,
    SantaSetup,
    ErrorPopUpModal,
  },
  methods: {
    submit() {
      this.displayForms = true;
    },
    add(val) {
      if (val.index !== this.counter) {
        this.counter++;
      }
      if (this.participantData[this.counter] === null) {
        this.participantData.push(val);
      } else {
        this.participantData[this.counter] = { ...val };
      }
    },
    error() {
      console.log("in error");
      this.problem = true;
    },
    validateTotal() {
      if (this.total > 50 || this.total < 3) {
        this.enableBtn = false;
        this.displayForms = false;
      } else {
        this.enableBtn = true;
      }
    },
    generate() {
      //call santa setup
      if (this.participantData.length !== 0) {
        this.valid = true;
      } else {
        console.log("empty data");
      }
    },
  },
};
</script>

<style scoped>
input {
  border: 1px solid grey;
  border-radius: 5px;
  height: 25px;
  margin-left: 10px;
  margin-right: 20px;
  text-align: center;
}

input[type="number"]::-webkit-inner-spin-button {
  opacity: 1;
}
.v-card__subtitle,
.v-card__text,
.v-card__title {
  padding: 15px;
}
.v-btn {
  margin: 15px;
}
</style>
