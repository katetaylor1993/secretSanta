<template>
  <v-container>
  <!-- Put whatever header you want up here! Any intro, any messages you want to show to introduce the user to the application -->
  <v-btn @click="showForm" />
  <MainForm v-if="agreed" />
  </v-container>
</template>

<script>
import MainForm from "../components/MainForm.vue";

export default {
  components: {
    MainForm,
  },
  data:() => ({
    agreed: false
  }),
  methods: {
    showForm(){
      this.agreed = true;
    }
  }
};
</script>
