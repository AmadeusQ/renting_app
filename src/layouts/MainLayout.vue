<template>
  <q-layout view="lHh Lpr lFf">
    <MainHeader />
    <SearchFilter class="q-mx-auto" />

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import MainHeader from "src/components/header/MainHeader.vue";
import SearchFilter from "src/components/SearchFilter.vue";
export default {
  name: "MainLayout",
  components: { MainHeader, SearchFilter },
};
</script>
