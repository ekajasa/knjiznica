<template>
  <q-page class="q-pa-md">
    <div class="text-h4 text-weight-bold q-mb-sm">Popis svih knjiga</div>
    <p class="text-subtitle1">Pregled svih knjiga u fondu knjižnice.</p>

    <q-table
      class="my-sticky-virtscroll-table"
      flat
      bordered
      virtual-scroll
      v-model:pagination="pagination"
      :rows-per-page-options="[0]"
      :virtual-scroll-sticky-size-start="48"
      row-key="id"
      :rows="rows"
      :columns="columns"
    />
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const columns = [
  {
    name: 'id',
    label: 'id',
    field: 'id',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'naslov',
    label: 'Naslov',
    field: 'naslov',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'autor',
    label: 'Autor',
    field: 'autor',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'godina',
    label: 'Godina',
    field: 'godina',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'zanr',
    label: 'Žanr',
    field: 'zanr',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  }
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

const pagination = ref({ rowsPerPage: 0 })
</script>

<style>
.my-sticky-virtscroll-table {
  height: 400px;
}
.my-sticky-virtscroll-table thead tr th {
  position: sticky;
  top: 0;
  z-index: 1;
  background-color: #fff;
}
</style>