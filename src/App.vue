<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
Vue Template</div>
    </v-app-bar>
    <v-content>
      <HelloWorld />
    </v-content>
  </v-app>
</template>
<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};

</script>
