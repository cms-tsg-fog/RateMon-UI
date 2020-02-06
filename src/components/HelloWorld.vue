<template>
  <v-container>
    <h1> Vue Template </h1>
  </v-container>
</template>
<script>
export default {
  name: 'HelloWorld',

  data: () => ({}),
  methods: {
    compute: function() {
      this.$axios.get('http://localhost:5000/', {
        params: {
          text: this.formText
        }
      }).then( function(response) {
        this.value = response.data.positive;
      });
    },
  },
};

</script>
