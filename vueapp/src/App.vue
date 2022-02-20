<template>
<!-- could also put in the header here, if you put it in here, use v-header or v-app-bar! -->
  <v-app>
    <v-main>
      <Home/>
    </v-main>
  </v-app>
</template>

<script>
import Home from './views/Home';

export default {
  name: 'App',

  components: {
    Home,
  },

  data: () => ({
    //
  }),
};
</script>
