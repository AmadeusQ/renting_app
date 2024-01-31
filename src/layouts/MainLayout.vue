<template>
  <q-layout view="lHh Lpr lFf">
    <MainHeader />

    <q-page-container class="container">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import MainHeader from "src/components/header/MainHeader.vue";
export default {
  name: "MainLayout",
  components: { MainHeader },
};
</script>
