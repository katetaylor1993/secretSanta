<template>
  <v-container>
    <v-dialog
      :value="showDialog"
      persistent
      transition="dialog-bottom-transition"
      max-width="600"
    >
      <v-card>
        <v-toolbar color="red" dark>{{ value.header }}</v-toolbar>
        <v-card-title> {{ value.message }}</v-card-title>
        <v-spacer></v-spacer>
        <v-card-subtitle>
          Press the button to return to initial form.
        </v-card-subtitle>
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
    showDialog: true,
  }),
  methods: {
    hidePopUp() {
      this.showDialog = false;
      this.$emit('closed');
    },
  },
};
</script>
