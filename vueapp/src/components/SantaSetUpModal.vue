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
      <div v-for="(email, index) in assignedArray" :key="index">
        <EmailModal :value="email" />
      </div>
    </div>
  </v-container>
</template>
<script>
import EmailModal from "./EmailModal.vue";

export default {
  props: ["value", "message"],
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
        to_name: "",
        to_email: "",
        general_message: "",
        assigned_name: "",
        assigned_details: "",
      },
      sortedArray: [],
      assignedArray: [],
    };
  },
  methods: {
    randomize() {
      //i will mess around with this and make it work
      //will make email object either loop hrough each email modal in a v-for for each in the data object
      //do a full objec twith everytwo and from, going through one will be easier to debug probably
      for (var x in this.value) {
        this.sortedArray.push(this.value[x]);
      }
      setTimeout(() => {
        this.randomizing = !this.randomizing;
      }, 3000);
      this.randomizeAlgorithm();
      this.assign();
    },
    randomizeAlgorithm() {
      for (var i = this.sortedArray.length - 1; i > 0; i--) {
        var j = Math.floor(Math.random() * (i + 1));
        var temp = this.sortedArray[i];
        this.sortedArray[i] = this.sortedArray[j];
        this.sortedArray[j] = temp;
      }
    },
    assign() {
      let len = this.sortedArray.length - 1;
      for (var i in this.sortedArray) {
        let tempObj = { ...this.emailObj };
        if (i == 0) {
          tempObj.to_name = this.sortedArray[0].name;
          tempObj.to_email = this.sortedArray[0].email;
          tempObj.general_message = this.message;
          tempObj.assigned_name = this.sortedArray[len].name;
          tempObj.assigned_details = this.sortedArray[len].about;
        } else {
          tempObj.to_name = this.sortedArray[i].name;
          tempObj.to_email = this.sortedArray[i].email;
          tempObj.general_message = this.message;
          tempObj.assigned_name = this.sortedArray[i - 1].name;
          tempObj.assigned_details = this.sortedArray[i - 1].about;
        }

        this.assignedArray.push(tempObj);
      }
      this.generated = true;
    },
  },
  mounted() {
    this.randomize();
  },
};
</script>
