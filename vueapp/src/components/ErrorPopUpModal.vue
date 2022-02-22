<template>
  <v-container>
    <v-dialog value="showDialog" transition="dialog-bottom-transition" max-width="600">
      <v-card>
        <v-toolbar color="red" dark>Error sending to: {{ problem }}</v-toolbar>
        <v-card-text>
          <div class="text-h2 pa-12">
            Press the button to return to initial form.
          </div>
        </v-card-text>
        <v-card-actions class="justify-end">
          <v-btn text @click="showDialog = false">Return</v-btn>
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
    showDialog: true
  }),
  methods: {
    generateError() {
      //this is where i will take in the value and display it properly
    },
  },
};
</script>
