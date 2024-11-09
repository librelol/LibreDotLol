<template>
  <v-container fluid>
    <v-row class="d-flex justify-center">
      <v-col
        v-for="(category, index) in categories"
        :key="index"
        cols="12"
        md="4"
        :style="category.links.length >= 3 ? 'max-height: 400px; overflow-y: auto;' : ''" 
      >
        <v-card
          elevation="2"
          class="formatted-card"
          @mouseover="hover = index"
          @mouseleave="hover = null"
        >
          <v-card-title class="text-center font-weight-bold">
            {{ category.title }}
          </v-card-title>
          <v-divider></v-divider>
          <v-list dense>
            <v-list-item
              v-for="(link, idx) in category.links"
              :key="idx"
              @click="handleLinkClick(link)"
              :class="{ 'hovered': hover === index }"
              :style="{ cursor: link.disclaimer ? 'pointer' : 'default' }"
            >
              <v-list-item-icon>
                <v-icon v-if="link.iconType === 'mdi'" :style="{ color: link.color || 'inherit' }">
                  {{ link.icon }}
                </v-icon>
                <img
                  v-else
                  :src="link.icon"
                  alt=""
                  class="icon"
                  :style="{ filter: link.color ? `invert(${link.color})` : 'none' }"
                />
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title class="font-weight-semibold">{{ link.name }}</v-list-item-title>
                <v-list-item-subtitle>{{ link.description }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-card>
      </v-col>
    </v-row>

    <!-- Confirmation Dialog -->
    <v-dialog v-model="dialog" max-width="500">
      <v-card>
        <v-card-title class="headline">Disclaimer</v-card-title>
        <v-card-text>{{ disclaimerText }}</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="green darken-1" text @click="confirmLink">Proceed</v-btn>
          <v-btn color="red darken-1" text @click="dialog = false">Cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  props: {
    categories: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      hover: null, // Track the hovered card
      dialog: false, // Manage dialog visibility
      disclaimerText: '', // Text to show in the dialog
      linkToOpen: null, // Store the link to open after confirmation
    };
  },
  methods: {
    handleLinkClick(link) {
      if (link.disclaimer) {
        this.disclaimerText = link.disclaimer; // Set the disclaimer text
        this.linkToOpen = link.url; // Store the link URL
        this.dialog = true; // Open the dialog
      } else {
        window.open(link.url, '_blank'); // Open the link directly if no disclaimer
      }
    },
    confirmLink() {
      if (this.linkToOpen) {
        window.open(this.linkToOpen, '_blank'); // Open the stored link
        this.dialog = false; // Close the dialog
      }
    },
  },
};
</script>

<style scoped>
.formatted-card {
  margin: 16px;
  transition: transform 0.3s, box-shadow 0.3s;
}

.formatted-card:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 30px rgba(0, 0, 0, 0.2);
}

.icon {
  width: 24px;
  height: 24px;
}
</style>
