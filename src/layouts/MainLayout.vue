<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title class="text-h4 text-weight-bold"> Knjižnica </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Essential Links </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.label"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from '@/components/EssentialLink.vue'

const linksList = [
  { title: 'Naslovnica', caption: 'Početna', icon: 'home', link: '#/' },
  { title: 'Popis knjiga', caption: 'Sve knjige', icon: 'menu_book', link: '#/popis_knjiga' },
  { title: 'Pretraživanje', caption: 'Traži knjigu', icon: 'search', link: '#/pretrazivanje' },
  { title: 'O nama', caption: 'Informacije', icon: 'info', link: '#/o_nama' },
  { title: 'Lokacija', caption: 'Karta', icon: 'place', link: '#/lokacija' },
  { title: 'Login', caption: 'Prijava', icon: 'login', link: '#/login' },
  { title: 'Registracija', caption: 'Novi korisnik', icon: 'person_add', link: '#/registracija' }
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
