<template>
  <q-page class="q-pa-md">
    <div class="text-h4 text-weight-bold q-mb-sm">Login</div>
    <p class="text-subtitle1">Prijavite se u svoj račun.</p>

    <div class="q-gutter-md" style="max-width: 400px">
      <q-input v-model="korisnickoIme" outlined label="Korisničko ime" />
      <q-input
        v-model="lozinka"
        outlined
        type="password"
        label="Lozinka"
        @keyup.enter="potvrdi"
      />

      <q-btn color="primary" label="Potvrdi" @click="potvrdi" />
    </div>

    <q-banner v-if="poruka" class="bg-grey-3 q-mt-md" style="max-width: 400px">
      {{ poruka }}
    </q-banner>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const korisnickoIme = ref('')
const lozinka = ref('')
const poruka = ref('')

function potvrdi () {
  if (!korisnickoIme.value || !lozinka.value) {
    poruka.value = 'Unesite korisničko ime i lozinku.'
    return
  }
  // ovdje će kasnije ići provjera u bazi
  poruka.value = 'Prijava poslana za korisnika: ' + korisnickoIme.value
}
</script>