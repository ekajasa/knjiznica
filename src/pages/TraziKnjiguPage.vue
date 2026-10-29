<template>
  <q-page class="q-pa-md">
    <div class="text-h4 text-weight-bold q-mb-sm">Pretraživanje</div>
    <p class="text-subtitle1">
      Upišite pojam i odaberite pretražuje li se po autoru ili po naslovu.
    </p>

    <div class="row items-center q-gutter-md q-mb-md">
      <q-input
        v-model="pojam"
        outlined
        label="Pojam za pretraživanje"
        style="min-width: 300px"
        @keyup.enter="trazi"
      />

      <q-checkbox v-model="poAutoru" label="Autor" />
      <q-checkbox v-model="poNaslovu" label="Naslov" />

      <q-btn color="primary" label="Traži" @click="trazi" />
    </div>

    <q-table
      v-if="pretrazeno"
      flat
      bordered
      title="Pronađene knjige"
      :rows="rezultati"
      :columns="columns"
      row-key="id"
      no-data-label="Nema pronađenih knjiga"
    />
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const columns = [
  { name: 'id', label: 'id', field: 'id', align: 'left', sortable: true,
    style: { fontSize: '14px' }, headerStyle: { fontSize: '18px' } },
  { name: 'naslov', label: 'Naslov', field: 'naslov', align: 'left', sortable: true,
    style: { fontSize: '14px' }, headerStyle: { fontSize: '18px' } },
  { name: 'autor', label: 'Autor', field: 'autor', align: 'left', sortable: true,
    style: { fontSize: '14px' }, headerStyle: { fontSize: '18px' } },
  { name: 'godina', label: 'Godina', field: 'godina', align: 'left', sortable: true,
    style: { fontSize: '14px' }, headerStyle: { fontSize: '18px' } },
  { name: 'zanr', label: 'Žanr', field: 'zanr', align: 'left', sortable: true,
    style: { fontSize: '14px' }, headerStyle: { fontSize: '18px' } }
]

const rows = [
  { id: 1, naslov: 'Zlatarovo zlato', autor: 'August Šenoa', godina: 1871, zanr: 'Roman' },
  { id: 2, naslov: 'Gospoda Glembajevi', autor: 'Miroslav Krleža', godina: 1928, zanr: 'Drama' },
  { id: 3, naslov: 'Povratak Filipa Latinovicza', autor: 'Miroslav Krleža', godina: 1932, zanr: 'Roman' },
  { id: 4, naslov: 'Ponornica', autor: 'Ivana Brlić-Mažuranić', godina: 1913, zanr: 'Bajka' },
  { id: 5, naslov: 'Priče iz davnine', autor: 'Ivana Brlić-Mažuranić', godina: 1916, zanr: 'Bajka' },
  { id: 6, naslov: 'Smrt Smail-age Čengića', autor: 'Ivan Mažuranić', godina: 1846, zanr: 'Ep' },
  { id: 7, naslov: 'Vlak u snijegu', autor: 'Mato Lovrak', godina: 1933, zanr: 'Roman za djecu' },
  { id: 8, naslov: 'Fališ mi', autor: 'Miljenko Jergović', godina: 2008, zanr: 'Roman' },
  { id: 9, naslov: 'Sarajevski Marlboro', autor: 'Miljenko Jergović', godina: 1994, zanr: 'Priče' },
  { id: 10, naslov: 'Kafkijada', autor: 'Zoran Ferić', godina: 2012, zanr: 'Roman' }
]

const pojam = ref('')
const poAutoru = ref(true)
const poNaslovu = ref(true)
const rezultati = ref([])
const pretrazeno = ref(false)

function trazi () {
  const q = pojam.value.trim().toLowerCase()

  rezultati.value = rows.filter(k =>
    (poAutoru.value && k.autor.toLowerCase().includes(q)) ||
    (poNaslovu.value && k.naslov.toLowerCase().includes(q))
  )
  pretrazeno.value = true
}
</script>