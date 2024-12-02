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

mQINBGc7iEIBEACeGf8Z835tPrJmOMTF3bcHakNOJyV0GnBvCsHMp6HnUAHStMNt
nNKGjB/KNXK9R/hd1MzDKYNsw3kmc0M4K9IAhyLMT0cRHcD5gM8LX/yUHW48iCWf
6FO6e8cEpkJDcs+2Ybew5I6a4tHfQyTIRmnNa2R164EHQZAMKxbNpE4wEqPhRNV/
UTF/9WtTMR+l9P++6Tpbt+M1k7dhVhycAJUCsD7izeMQ1qQyHJvOFTrVAbVqZIdI
BPi+uM4StkUJZZBM34nfBuZcalPuuwIa6jtWdYDJPvcLZzMmBomcD+q5nxhLSWxo
13OMDWwW9DqJUxX63DYk6WDRS3zMHxN+/33YGSEdWLk54lLSrxR3buj0J+uVfs4Y
/gRjHIUuDWsU8IbSRW8zm9stjQUa/wf2Qww81aqrHD/T/26Q6v7pqJdW+JFU/7//
5U5HWAZ8lerMnLyLMSi/gtZQMv0TsZToZflfQ5M8udDM0lq/XTk9SjxiMnBAQ283
b/OHRqms1tduqa2oJnmzpFRDRC7L9q502kXIaXT9ME/fZe3DKAOBsClWOl4kPUYE
/L4eByK3vjiHSGW5wU+s0CQ0p1VvgoXJa8cuiopBtz2qu8UiaZ0SSlSTT956jIiO
u9+lbUGabbu2YYKhq52wgimc3euTMpRSVeDaKL5AIkusAFfXnTjKPcyd0QARAQAB
tBtMaWJyZSBMb2wgPGhlbGxvQGxpYnJlLmxvbD6JAlEEEwEIADsWIQTmeCwi8hlV
OEdG8/GrkuJKcw7kHAUCZzuIQgIbAwULCQgHAgIiAgYVCgkICwIEFgIDAQIeBwIX
gAAKCRCrkuJKcw7kHOaXD/9/UohUnGjXaeqDgyZNsYch5pxXoUvIGJurXn/6cKSf
RGZ8eJ+28ePk/NDExo9IPIJutxlQeZGfEp9c86ue623qbrAmME3xB0a09+xovBdw
mYX5MaoprDfwYOZRpoPQqqHnvLZYaSUHP+iQj2kmS9QNTvvMnjB/rtYkO1LbKsl2
HiHakPilIcY6svgAx4LDlrN42ZyoDBMPrGoInWLmDM76w/dRsNe0Eq1/3Dmht4te
P5Ow110wlQhJdNU3ld7Y1vS+i0hVq6Nifx43tG1RkHScJmMXCQkRhkGcmj64zgEM
pCAyFibDM5Eg62XSSUVhsRwRM5rg4Od6zfYxRHbxyHq4YuBQhilZ3wUb2b+FMitw
Nsc0DjoP5cc6gvCUFpFZkycqUi+20gvmKvtsMVdbfpvs1xt6tzHgIzDmOfAsMEke
UDzljCC39PyAm4JBNlkbFQGNs6Tk9WI8wJj3mfTJHJCZlzVfFd3swLI3qm7sXGH1
nLvcgC9nGvP6MeeT4sMyIAwyRMBwWP8VyduY4lkVAgpZcc0Zf1l5e7+UI/ag1WCa
BRFrtsJb8HLFtvTLjSsM0tjFNQN9xUzVvk/34+YdQidO4tAwAMX9pM8WrnbJuVmG
K0ZKQDn1aVMX80ApLDShobCxKmOk6+fJvuJKUrsSTPd5Zoi+JC168JSKl9+9BtHD
jbkCDQRnO4hCARAA15/RspGh/77+V+jgdUACVpxIreF7TMMtoSO/fwtQa0d1aGX4
NdDOEjtDdicMSZh72oBsaknWGRGUmrrm0zGTnZNwIxhb43soiLiHOMSZEfEWwzPf
hvw4DRKIw07mBrMUDXtiRsp+laFU+jHHXcPfAHAby5T/us857iny2kkZFztWPbFp
vHhOPaClZEA5kTcBTcw3rRyI37qnRnX+p3FNuaOOWUtaSTCwYd9N3ScYiO7vx7Gv
oYp0nrvZcuGVbo0uiF2K0Er/SdTIz+srkrD+2NmWKDe/WhsxxwEgDx1l6SfbMNV1
oXmy6vfeHJXLAfJaYJT+uzAynw/cuoBJ2U1eIxVXu52SPKRg2y+y/3eNSLMslZhi
2NH0XCzyGABjX+gt+haNCLWwER8EdxFKfcF8CMerSdaUSCPi/blE8JlMPKjC/Qsf
NcIt5aBkWmV1s4hHpfLJbj28cmGAeTQhhcEc2xaYRGY+1rD9mVj08kgF2vyQRKV1
h1s4IBk3tuGHuVoiH5f8wJC3eq8NEKKqWN9c07BDCyCR+gM8Kzxrfu4+096msboJ
HJWaI9K1D+NCanSAwfwW0NLTSFJh+sidLyQCix50Nz/fkVnOboHfZAM4DtvivYjn
YgHkLFHG7feB+HLrta+h91aQAYSmpHKEVxWjU29H0g+bgK4EQEiZyHLO1NsAEQEA
AYkCNgQYAQgAIBYhBOZ4LCLyGVU4R0bz8auS4kpzDuQcBQJnO4hCAhsMAAoJEKuS
4kpzDuQcOTMP/3oIgVg5kGd34Kv3rQPvDmrfHPxCqcpuD+RrwuseBqij1SvKtBe8
Tk6YyGahZSigKkQo4NA7WH7aHJJuUHvQgUFGlrM/8ov09EWttB+LP98KdM+OWauX
W2LMziVpEdhd77pzK+9tXHoVYt4DnOT0kIQ3wb4BUQdc3Sas54V6pWhgj463acSS
aE7HL2uMU/aDL1VWFvbqc7fo4+vSSke++ZqHcEIcP8xOXPoZo4DQ18z11fG2SgVc
o5NyUO1blRkQqsh3jAwZPJKuClQRymAmqf8cFJ/1hxarOueOiPKvMCPbsjZy6nCz
4BCt9T1SqcUnkctgimharC7Yd4coSB5y5XP6mQUPP1izDj0wg5Ciebt6aHUH4lzF
7/Uj/99/9DCqQYMseG9eJKptcCSehcpz9QTxNQB8xhzaW1AW3sx1nuGSH75q008j
y3Lk9yq9EUvWdtgMcF4trQpXAI/PNRXPPlURShTISHAdT1eDB8UojESdQJsn+yeT
/O4WEbzK2gheDLoY5z+QJ7PGIgCNihhqZpB570vPH0MjbRPIeMrGH361RPXYGMCx
hdsoM0WK4M6njinTSluRLB/xx7B6jR9+u7QKkpRpy6KKskETLqM6hQudNS8WVwTX
sy5xR0PmRTsukoB5jYzijqvhoNhp5PNaub8Nm65DskypU5fYpFxGHLrD
=jwHb
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
