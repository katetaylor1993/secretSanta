<template>
  <v-container>
    <v-dialog
      :value="showDialog"
      persistent
      transition="dialog-bottom-transition"
      max-width="600"
    >
      <v-card>
        <v-toolbar color="red" dark>Error sending to: {{ problem }}</v-toolbar>
        <v-card-title>
          Press the button to return to initial form.
        </v-card-title>
        <v-card-actions class="justify-end">
          <v-btn dark @click="hidePopUp">Return</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  props: ["value"],
  data: () => ({
    problem: "random@email.com",
    showDialog: true,
  }),
  methods: {
    generateError() {
      //this is where i will take in the value and display it properly
    },
    hidePopUp() {
      this.showDialog = false;
    },
  },
};
</script>
