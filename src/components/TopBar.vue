<template>
    <v-app-bar app color="red" dark elevate-on-scroll>
        <v-toolbar-title class="title">
            <v-btn text href="/">LibreLol</v-btn>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-menu offset-y>
            <template v-slot:activator="{ props }">
                <v-btn icon v-bind="props">
                    <v-icon>mdi-menu</v-icon>
                </v-btn>
            </template>
            <v-list>
                <v-list-item>
                    <v-list-item-title>
                        <v-btn block href="https://uptime.libre.lol/status/services" class="button">Uptime</v-btn>
                    </v-list-item-title>
                </v-list-item>
                <v-list-item>
                    <v-list-item-title>
                        <v-btn block href="/tos" class="button">Terms of Service</v-btn>
                    </v-list-item-title>
                </v-list-item>
                <v-list-item>
                    <v-list-item-title>
                        <v-btn block href="https://git.libre.lol/librelol/FrontendWebsite" class="button">Source Code</v-btn>
                    </v-list-item-title>
                </v-list-item>
                <v-list-item>
                    <v-list-item-title>
                        <v-btn block href="https://libre.lol/email" class="button">Email</v-btn>
                    </v-list-item-title>
                </v-list-item>
            </v-list>
        </v-menu>
    </v-app-bar>
</template>

<script>
export default {
    name: 'TopBar',
};
</script>

<style scoped>
.button {
    width: 100%; /* Ensure buttons take full width */
    justify-content: flex-start; /* Align text to the start */
}
</style>
