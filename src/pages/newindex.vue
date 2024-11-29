<template>
    <v-container class="fill-height d-flex justify-center align-center">
      <v-row class="justify-center align-center fill-height">
        <v-col cols="12" sm="8" md="6">
          <v-card class="text-center pa-4">
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
              <v-hover v-slot:default="{ isHovering }">
                <v-btn 
                  :color="isHovering ? 'primary darken-2' : 'primary'" 
                  href="/services" 
                  class="my-2"
                >
                  Our Services
                </v-btn>
              </v-hover>
              <v-hover v-slot:default="{ isHovering }">
                <v-btn 
                  :color="isHovering ? 'error darken-2' : 'error'" 
                  href="/threatmodel" 
                  class="my-2"
                >
                  Threat Model Quiz (Alpha)
                </v-btn>
              </v-hover>
              <v-hover v-slot:default="{ isHovering }">
                <v-btn 
                  :color="isHovering ? 'success darken-2' : 'success'" 
                  href="/apps" 
                  class="my-2"
                >
                  Recommended Services
                </v-btn>
              </v-hover>
              <v-hover v-slot:default="{ isHovering }">
                <v-btn 
                  :color="isHovering ? 'warning darken-2' : 'warning'" 
                  href="https://cloud.libre.lol"
                  class="my-2"
                >
                  Libre Cloud (NextCloud)
                </v-btn>
              </v-hover>
              <v-card-title class="card-title">
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
    </v-container>
  </template>
  
  <script>
  import Categories from '../categories_social.json'; // Adjust the path as necessary
  import config from '@/config_index.json'; // Change the path to the JSON file
  
  export default {
    data() {
      return {
        Categories,
        titles: config.titles,
        randomTitle: '',
        alertEnabled: config.alert.enabled,
        alertMessage: config.alert.message,
      };
    },
    mounted() {
      this.setRandomTitle();
      this.interval = setInterval(this.setRandomTitle, 300000); // 300000 ms = 5 minutes
    },
    beforeDestroy() {
      clearInterval(this.interval);
    },
    methods: {
      setRandomTitle() {
        const randomIndex = Math.floor(Math.random() * this.titles.length);
        this.randomTitle = this.titles[randomIndex];
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