<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Our Services</h1>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <Widgets :categories="Categories" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Categories from '../categories_services.json'; // Adjust the path as necessary

export default {
  data() {
    return {
      Categories,
    };
  },
};
</script>