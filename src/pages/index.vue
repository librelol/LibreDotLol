<template>
  <v-container class="fill-height d-flex justify-center align-center">
    <v-row class="justify-center align-center fill-height">
      <v-col cols="12" sm="8" md="6">
        <v-card class="text-center pa-4">
          <!-- Move the alert inside the card -->
          <v-alert color="red" v-if="alertEnabled" type="info" border="left" class="mb-4">
            {{ alertMessage }}
          </v-alert>

          <v-img 
            src="@/assets/meme.jpg" 
            alt="Meme image" 
            class="mb-4" 
            height="200px" 
            contain
          ></v-img>
          <div class="d-flex flex-column align-center">
            <v-btn 
              color="blue" 
              href="/services" 
              class="my-2" 
              width="250"
            >
              Our Services
            </v-btn>
            <v-btn 
              color="red" 
              href="/threatmodel" 
              class="my-2" 
              width="250"
            >
              Threat Model Quiz (Alpha)
            </v-btn>
            <v-btn 
              color="green" 
              href="/apps" 
              class="my-2" 
              width="250"
            >
              Recommended Services
            </v-btn>
            <v-btn 
              color="purple" 
              @click="showWidgets = true" 
              class="my-2" 
              width="250"
            >
              Social
            </v-btn>
            <v-btn 
              color="yellow" 
              href="https://cloud.libre.lol"
              class="my-2" 
              width="250"
            >
              Libre Cloud (NextCloud)
            </v-btn>
            <v-btn 
              color="orange" 
              @click="toggleRandomTitle" 
              class="my-2" 
              width="250"
            >
              Toggle Random Title
            </v-btn>
            <v-card-title class="card-title" v-if="showRandomTitle">
              {{ randomTitle }}
            </v-card-title>
            <v-card-text>
              <p>
                Welcome to Libre.lol, I like to make three letter agencies and corporations cry. Use my own self-hosted services or ones I recommend. I am a privacy advocate and I believe in freedom of speech.
              </p>
              <p>
                Our servers restart at 3 AM GMT
              </p>
            </v-card-text>
          </div>
        </v-card>
      </v-col>
    </v-row>
    <v-dialog v-model="showWidgets">
      <Widgets :categories="Categories" />
      <div class="d-flex justify-center">
        <v-btn color="red darken-1" max-width="600px" text @click="showWidgets = false">Close</v-btn>
      </div>
    </v-dialog>
  </v-container>
</template>

<script>
import Widgets from '@/components/Widgets.vue';
import Categories from '../categories_social.json'; // Adjust the path as necessary
import config from '@/config_index.json'; // Change the path to the JSON file

export default {
  data() {
    return {
      Categories,
      showWidgets: false,
      titles: config.titles,
      randomTitle: '',
      alertEnabled: config.alert.enabled,
      alertMessage: config.alert.message,
      showRandomTitle: false, // New data property
    };
  },
  mounted() {
    this.setRandomTitle();
  },
  methods: {
    setRandomTitle() {
      const randomIndex = Math.floor(Math.random() * this.titles.length);
      this.randomTitle = this.titles[randomIndex];
    },
    toggleRandomTitle() {
      this.showRandomTitle = !this.showRandomTitle;
    }
  }
}
</script>

<style scoped>
.fill-height {
  height: 100vh;
}

.card-title {
  white-space: normal; /* Allow text to wrap */
  word-wrap: break-word; /* Break long words if necessary */
  overflow-wrap: break-word; /* Similar to word-wrap */
}
</style>
