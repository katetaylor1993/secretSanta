<template>
  <div>
    <!-- <h1>Participant Forms</h1>
        <p>Please enter each participant's name, email, and a short description of them below:</p> -->
    <v-form ref="form" v-model="valid">
      <v-text-field
        v-model="formData.name"
        :rules="[rules.checknameSize]"
        label="Name"
        counter
        maxlength="256"
      ></v-text-field>
      <v-text-field
        v-model="formData.email"
        :rules="[rules.checkEmail]"
        label="Email"
      ></v-text-field>
      <v-text-field
        v-model="formData.about"
        :rules="[rules.checkAbout]"
        label="About"
        counter
        maxlength="3000"
      ></v-text-field>
    </v-form>
  </div>
</template>

<script>
export default {
  // props: {
  //   form: Object
  // },
  watch: {
    formData: {
      deep: true,
      immediate: true,
      handler: function (val) {
        //  this.$emit("input", val)
        var participant = new Object();
        if ((this.$refs.form as Vue & { validate: () => boolean }).validate()) {
          participant = { ...val };
          this.$emit("add", participant);
        } 
        else {
          console.log("one is blank");
        }
      },
    },
  },
  computed: {
  form(): Vue & { validate: () => boolean } {
    return this.$refs.form as Vue & { validate: () => boolean }
  }
},
  data() {
    return {
      valid: false,
      formData: {
        name: "", //no NULL 256 Max
        email: "", //Input rule needed
        about: "", // so No check 3000 Max
      },
      rules: {
        checknameSize: (value) =>
          (value.length <= 256 && value.length > 0) ||
          "Name too long or too short", //Works
        checkEmail: (value) => /.+@.+/.test(value) || "Invalid Email", //Works
        checkAbout: (value) =>
          value.length <= 3000 || "Too many words sum it up", //Works
        //Gonna need 3 input rules
      },
    };
  },

  // methods: {
  //   validate() {
  //     this.$refs.form.validate();
  //   }
  // }

};
</script>

<style>

</style>
