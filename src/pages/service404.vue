<template>
  <v-app>
    <v-container class="text-center">
      <!-- Main Error Message -->
      <v-row justify="center" class="mt-5">
        <v-col cols="12" md="8" lg="6">
          <v-alert type="error" elevation="2" class="mb-5" border="left">
            <v-icon left>mdi-alert-circle-outline</v-icon>
            <div>
              <h2 class="headline">404 - Page Not Found</h2>
              <p>Sorry, the service you are trying to access doesn't exist or is currently down.</p>
              <p>If you are certain that the service exists, please check back later or check our socials for any updates. Which they can be found on our home page.</p>
            </div> <!-- Missing closing div -->
          </v-alert> <!-- Closing the v-alert tag -->
        </v-col>
      </v-row>

      <!-- Optional: Back to Home Button -->
      <v-row justify="center">
        <v-col cols="12" md="8" lg="6">
          <v-btn color="primary" @click="goHome">
            Back to Home
          </v-btn>
        </v-col>
      </v-row>

      <!-- Displaying Referrer Info (for Debugging) -->
      <v-row justify="center" class="mt-5">
        <v-col cols="12" md="8" lg="6">
          <v-alert type="info" elevation="2" class="mb-5" border="left">
            <v-icon left>mdi-information-outline</v-icon>
            <div>
              <h4 class="headline">Referrer Info:</h4>
              <p>{{ referrer ? `You came from: ${referrer}` : 'No referrer available.' }}</p>
            </div>
          </v-alert>
        </v-col>
      </v-row>

    </v-container>
  </v-app>
</template>

<script>
export default {
  name: 'NotFoundPage',
  data() {
    return {
      referrer: document.referrer || null, // Capture the referrer URL (if available)
    };
  },
  methods: {
    goHome() {
      this.$router.push('/');
    }
  },
  mounted() {
    // Optionally, you could send the referrer to your analytics service or log it
    if (this.referrer) {
      console.log('Visitor came from:', this.referrer); // Log the referrer to the console (for debugging purposes)
      // You could send this information to a server, analytics service, etc.
    }
  }
}
</script>

<style scoped>
.v-alert {
  background-color: #ffebee;
  color: #b71c1c;
}
</style>
