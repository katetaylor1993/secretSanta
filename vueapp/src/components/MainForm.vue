<template>
  <v-container>
    <v-card style="background-color: #ddffd1; border-color: #015a2c; border-style: solid; border-width: 3px;"
    light>
      <v-row justify="center">
        <v-card-title
          >Number of Participants:
          <input type="number" v-model="total" @input="validateTotal" />
          Enter a general message:
          <input v-model="message" @input="validateTotal" />
          <v-btn color="#B71C1C" style="color: white" :disabled="!enableBtn" @click="submit"
            >Submit</v-btn
          >
        </v-card-title>
      </v-row>
      <v-card style="background-color: #E57373" v-if="displayForms">
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
            <v-btn color="#015a2c" style="color: white" @click="generate">Generate</v-btn>
          </v-row>
        </v-col>
      </v-card>

      <div v-if="valid">
        <SantaSetup :value="participantData" :message="message" />
      </div>
      <div v-if="popUp">
        <PopUpModal :value="modalMsg" @closed="popUp = false" />
      </div>
    </v-card>
  </v-container>
</template>

<script>
import ParticipantForm from "./ParticipantForm.vue";
import SantaSetup from "./SantaSetUpModal.vue";
import PopUpModal from "./PopUpModal.vue";

export default {
  data() {
    return {
      total: 0,
      valid: false, //this will be an object bound to the table/form created to pass in to the santaSetup, they shoudl be validated from the participant form
      //this will be filled dynamically
      participantData: [],
      popUp: false,
      enableBtn: false,
      displayForms: false,

      modalMsg: { header: "", message: "" },
      error: false,
      message: "",
    };
  },
  components: {
    ParticipantForm,
    SantaSetup,
    PopUpModal,
  },
  methods: {
    submit() {
      this.displayForms = true;
    },
    add(val) {
      if (this.participantData[val.index] === null) {
        this.participantData.push(val);
      } else {
        this.participantData[val.index] = { ...val };
      }
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
      //call santa setup if all slots are filled

      if (this.participantData.length === 0) {
        return;
      }
      this.participantData = this.participantData.filter((a) => a !== " ");

      let nameArr = this.participantData.map(function (item) {
        return item.name;
      });
      let nameDup = nameArr.some(function (item, idx) {
        return nameArr.indexOf(item) != idx;
      });
      let emailArr = this.participantData.map(function (item) {
        return item.email;
      });
      let emailDup = emailArr.some(function (item, idx) {
        return emailArr.indexOf(item) != idx;
      });

      if (parseInt(this.total) !== this.participantData.length) {
        this.modalMsg = {
          header: "Error!",
          message: "Not all forms are filled or valid, fix this and try again.",
        };
        this.popUp = true;
      } else if (nameDup === true) {
        this.modalMsg = {
          header: "Error!",
          message: "There is a duplicate name, fix this and try again.",
        };

        this.popUp = true;
      } else if (emailDup === true) {
        this.modalMsg = {
          header: "Error!",
          message: "There is a duplicate email, fix this and try again.",
        };

        this.popUp = true;
      } else {
        this.valid = true;
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
