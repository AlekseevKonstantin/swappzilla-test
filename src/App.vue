<template>
  <v-app>
    <v-content>
      <FundYourAcc v-model="dialog" />
      <v-btn color="primary" class="mt-10 mx-auto" dark @click="dialog = true" style="display: block;">Open Dialog</v-btn> 
    </v-content>
  </v-app>
</template>

<script>
import FundYourAcc from './components/FundYourAcc';

export default {
  name: 'App',
  dialog: false,
  components: {
    FundYourAcc,
  },

  data: () => ({
    dialog: false
  }),

};
</script>
