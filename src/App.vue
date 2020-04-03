<template>
  <v-app>
    <v-content>
      <FundYourAcc/>
    </v-content>
  </v-app>
</template>

<script>
import FundYourAcc from './components/FundYourAcc';

export default {
  name: 'App',

  components: {
    FundYourAcc,
  },

  data: () => ({
    //
  }),
};
</script>
