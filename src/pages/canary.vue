<template>
  <v-container class="d-flex justify-center align-center" style="height: 90vh;">
    <v-card max-width="600" class="pa-4">
      <v-card-title>
        <v-icon class="mr-2">mdi-shield-check</v-icon>Security Notice
      </v-card-title>

      <v-card-subtitle>
        <strong>Last updated: 11/16/2024 (MM/DD/YYYY)</strong>
      </v-card-subtitle>

      <v-card-text>
        <p>This page is an important indicator of the security and integrity of our services.</p>
        <p>If this page is <strong>removed</strong> or has <strong>not been updated within the last 30 days</strong>, 
        please <strong>immediately discontinue use of our services</strong>. This could signal a potential compromise of our systems, 
        but might also not.</p>
      </v-card-text>

      <v-btn @click="redirectToEmailPage" color="primary">Go to Email Page to Download our Public Key</v-btn>
    </v-card>
  </v-container>
</template>

<script>
export default {
  methods: {
    redirectToEmailPage() {
      // Redirecting to the /email route
      this.$router.push('/email');
    }
  }
};
</script>

<style scoped>
.v-card {
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}
</style>
