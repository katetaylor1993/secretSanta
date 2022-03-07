<template>
  <v-container>
  <!-- Put whatever header you want up here! Any intro, any messages you want to show to introduce the user to the application -->
  <v-row>
    <v-app-bar
     style="border-radius: 10px"
     src="https://dm0qx8t0i9gc9.cloudfront.net/thumbnails/video/yRF5c-O/snow-flakes-falling-seamless-loop-red-motion-background_blx_xrhme_thumbnail-1080_01.png"
    >
      <v-toolbar-title 
      class="title_text"><h1>Secret Santa</h1></v-toolbar-title>
    </v-app-bar>
  </v-row>
  <v-row>
    <p class="intro">Start by hitting "click here to start". Enter in 3 to 50 participants with a general message that will be sent to everyone, then hit submit.
         Participant forms will pop up and we will need you to input each participants name, their valid email, and information that describes their likes/dislikes and what they would want for Christmas this year.
          After all the info is in hit the "generate" button.</p>
  </v-row>
  <v-row
    justify="space-around"
  >
    <v-btn 
      @click="showForm"
      color="#015a2c"
      title
      depressed
    > 
    <p>Click here to start</p>
    </v-btn>
  </v-row>
  <v-row>
    <MainForm v-if="agreed" />
  </v-row>
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

<style>
  h1 {
    font-weight: 400;
    color:#015a2c;
    border-radius: 10px;
  }
  .intro{
    text-align: center;
    color: black;
    border-style: solid;
    border-color: #015a2c;
    margin-top: 20px;
    border-radius: 10px;
    padding-top: 8px;
    padding-left: 50px;
    padding-right: 50px;
    height: 100px;
    font-size: 18px;
    background-color: #ddffd1;
  }
  p{
    height: 1px;
    text-align: center;
    color: rgb(255, 255, 255)
  }
</style>