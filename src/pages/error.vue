<template>
    <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
            <v-col class="text-center">
                <v-icon size="64" color="error">mdi-alert-circle</v-icon>
                <h1 class="display-1">Error</h1>
                <p class="subheading">The page or service you tried to visit doesn't exist or is down</p>
                <v-btn color="primary" @click="goHome">Go to Home</v-btn>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    methods: {
        goHome() {
            this.$router.push('/');
        }
    }
}
</script>

<style scoped>
.fill-height {
    height: 100vh;
}
</style>