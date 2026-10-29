<template>
  <q-page class="q-pa-md">
    <div class="text-h4 text-weight-bold q-mb-sm">Registracija</div>
    <p class="text-subtitle1">Kreirajte novi korisnički račun.</p>

    <div class="q-gutter-md" style="max-width: 400px">
      <q-input v-model="korisnik.ime" outlined label="Ime" />
      <q-input v-model="korisnik.prezime" outlined label="Prezime" />
      <q-input v-model="korisnik.korisnickoIme" outlined label="Korisničko ime" />
      <q-input v-model="korisnik.email" outlined type="email" label="E-mail" />
      <q-input v-model="korisnik.lozinka" outlined type="password" label="Lozinka" />

      <q-btn color="primary" label="Potvrdi" @click="potvrdi" />
    </div>

    <q-banner v-if="poruka" class="bg-grey-3 q-mt-md" style="max-width: 400px">
      {{ poruka }}
    </q-banner>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const korisnik = ref({
  ime: '',
  prezime: '',
  korisnickoIme: '',
  email: '',
  lozinka: ''
})
const poruka = ref('')

function potvrdi () {
  const k = korisnik.value
  if (!k.ime || !k.prezime || !k.korisnickoIme || !k.email || !k.lozinka) {
    poruka.value = 'Ispunite sva polja.'
    return
  }
  // ovdje će kasnije ići spremanje u tablicu korisnik
  poruka.value = 'Registracija poslana za korisnika: ' + k.korisnickoIme
}
</script>