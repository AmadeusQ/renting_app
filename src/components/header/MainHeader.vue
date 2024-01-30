<template>
  <q-header class="q-py-sm custom-header">
    <q-toolbar class="q-px-md">
      <q-btn class="header-logo" padding="none" flat :to="{ path: '/' }">
        Domus
      </q-btn>
      <q-space></q-space>
      <div class="flex q-mx-md">
        <q-btn :label="$t('sale')" flat class="q-px-sm q-mr-xl" color="black" />
        <q-btn :label="$t('rent')" flat class="q-px-sm q-ml-xl" color="black" />
      </div>
      <q-space />
      <div class="flex items-center q-mr-md">
        <q-btn
          label="ҚАЗ"
          flat
          class="q-px-sm q-mr-xs"
          @click="changeLang('kk')"
          :class="lang === 'kk' && 'active-lang-btn'"
          style="color: grey"
        />
        <q-btn
          label="EN"
          flat
          class="q-px-sm q-mr-xs"
          @click="changeLang('en')"
          :class="lang === 'en' && 'active-lang-btn'"
          style="color: grey"
        />
        <q-btn
          label="РУС"
          flat
          class="q-px-sm"
          @click="changeLang('ru')"
          :class="lang === 'ru' && 'active-lang-btn'"
          style="color: grey"
        />
      </div>
      <q-separator vertical color="black" />
      <div class="flex items-center">
        <q-btn
          :label="$t('signIn')"
          flat
          color="black"
          class="q-px-sm q-mx-md"
        />
        <q-btn :label="$t('signUp')" flat color="black" class="q-px-sm" />
      </div>
    </q-toolbar>
  </q-header>
</template>

<script>
import { Cookies } from "quasar";

export default {
  name: "MainHeader",
  mounted() {
    this.lang = this.$i18n.locale;
    console.log(this.lang);
  },
  data() {
    return {
      lang: this.$i18n.locale,
    };
  },
  methods: {
    changeLang(lang) {
      this.lang = lang;
      this.$i18n.locale = lang;
      Cookies.set("tscLocale", lang);
      window.location.reload();
    },
  },
};
</script>

<style scoped>
.q-btn {
  text-transform: capitalize;
}
.custom-header {
  background-color: #fff;
  color: #000;
  border-bottom: 1px solid #000;
}
.header-logo {
  text-decoration: none;
  font-weight: bold;
  cursor: pointer;
  color: #000 !important;
  font-size: 26px;
}
.active-lang-btn {
  color: #000 !important;
}
</style>
