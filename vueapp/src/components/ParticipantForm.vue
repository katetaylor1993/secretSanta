<template>
  <v-container>
    <v-form ref="form" v-model="valid">
      <v-card light>
        <v-row>
          <v-col>
            <v-card-title style="color: black"
              >Participant #{{ index }}:</v-card-title
            >
          </v-col>
        </v-row>
        <v-card-text>
          <v-row>
            <v-col>
              <v-text-field
                v-model="formData.name"
                :rules="[rules.checknameSize]"
                label="Name"
                counter
                maxlength="256"
              ></v-text-field> </v-col
            ><v-col>
              <v-text-field
                v-model="formData.email"
                :rules="[rules.checkEmail]"
                label="Email"
              ></v-text-field> </v-col
            ><v-col>
              <v-text-field
                v-model="formData.about"
                :rules="[rules.checkAbout]"
                label="About"
                counter
                maxlength="3000"
              ></v-text-field
            ></v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-form>
  </v-container>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  props: { index: Number },
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
        checkEmail: (value) =>
          /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value) || "Invalid Email", //Works
        checkAbout: (value) =>
          value.length <= 3000 || "Too many words, sum it up", //Works
        //Gonna need 3 input rules
      },
    };
  },
  watch: {
    formData: {
      deep: true,
      handler: function (val) {
        if (this.$refs.form.validate()) {
          this.formData = { index: this.index, ...val };
          this.$emit("add", this.formData);
        }
      },
    },
  },
});
</script>

<style scope>
.theme--light.v-card > .v-card__text {
  padding-top: 1px;
  margin-top: 1px;
}
</style>
