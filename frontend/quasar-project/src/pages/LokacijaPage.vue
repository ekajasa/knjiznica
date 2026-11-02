<template>
  <q-page class="q-pa-md">
    <div class="text-h4 text-weight-bold q-mb-sm">Lokacija</div>
    <p class="text-subtitle1">
      Gradska knjižnica Rijeka nalazi se u središtu grada. Dobro došli!
    </p>

    <div id="map" style="height:500px;"></div>
  </q-page>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import * as L from 'leaflet'
import 'leaflet/dist/leaflet.css'

const initialMap = ref('')

onMounted(() => {
  initialMap.value = L.map('map').setView([45.3312, 14.4322], 13)

  L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy;<a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  }).addTo(initialMap.value)

  L.circleMarker([45.3312, 14.4322], { radius: 10, color: '#5d4037' })
    .addTo(initialMap.value)
    .bindPopup('Gradska knjižnica Rijeka')
})
</script>