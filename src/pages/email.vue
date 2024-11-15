<template>
    <v-container class="pa-5">
        <v-row>
            <v-col cols="12" md="8" offset-md="2">
                <v-card elevation="2" class="pa-4">
                    <v-card-title class="font-weight-bold text-center">
                        Contact Information
                    </v-card-title>
                    <v-divider></v-divider>
                    <v-card-text>
                        <div class="text-center">
                            <p>
                                <strong>Email:</strong> <a :href="`mailto:${email}`">{{ email }}</a>
                            </p>
                            <p>
                                <strong>PGP Key:</strong>
                            </p>
                            <pre class="pgp-key">{{ pgpKey }}</pre>
                        </div>
                    </v-card-text>
                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn color="blue" @click="downloadPGPKey">
                            Download PGP Key
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: 'ContactInfo',
    data() {
        return {
            email: 'hello@libre.lol', // Replace with your email
            pgpKey: `
-----BEGIN PGP PUBLIC KEY BLOCK-----

mDMEZze8JBYJKwYBBAHaRw8BAQdA0j5cLKAi+4yrG4/LerMmJWoWPAefLNFv67BE
9ZluGAi0G0xpYnJlIExvbCA8aGVsbG9AbGlicmUubG9sPoiZBBMWCgBBFiEEowsF
bKb6Pz6671afSyVXiRO01FYFAmc3vCQCGwMFCQWjXGwFCwkIBwICIgIGFQoJCAsC
BBYCAwECHgcCF4AACgkQSyVXiRO01FbrZgD/cOiir/22l4Ly/CM9EpJ0BfWwDWPd
taYX3RwpyHCVQWAA+gIKLEXIhd4q3rEa3c7fHZtuOHTG+I9n+Vt/l7Hvii4KuDgE
Zze8JBIKKwYBBAGXVQEFAQEHQE7GVbelO9LpknnPZT24xXkxM0LAnnQPeHvBjiuP
jNxUAwEIB4h+BBgWCgAmFiEEowsFbKb6Pz6671afSyVXiRO01FYFAmc3vCQCGwwF
CQWjXGwACgkQSyVXiRO01FYSeAEAmBDnRMs7xTNVGYDGEL6XTaNw4Spm37msnw+A
fHaKUrcA/24gWiQFBmCnVPaWF7vwhS8CwVPFbGWgROYSEQ30jxEL
=Osbl
-----END PGP PUBLIC KEY BLOCK-----
`,
        };
    },
    methods: {
        downloadPGPKey() {
            const blob = new Blob([this.pgpKey], { type: 'text/plain' });
            const link = document.createElement('a');
            link.href = window.URL.createObjectURL(blob);
            link.download = 'librelol.asc';
            link.click();
        },
    },
};
</script>

<style scoped>
.pgp-key {
    border: 1px solid #ccc;
    padding: 10px;
    border-radius: 4px;
    white-space: pre-wrap; /* Keeps formatting of the PGP key */
    overflow: auto; /* Allows scrolling if necessary */
}
</style>
