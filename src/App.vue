<template>
  <router-view />
</template>

<script>
import "moment/locale/kk";
import "moment/locale/ru";
import { Cookies } from "quasar";
import moment from "moment";

export default {
  name: "App",
  methods: {
    checkLang() {
      const lang = Cookies.get("tscLocale");
      if (lang) {
        this.$i18n.locale = lang;
      } else {
        Cookies.set("tcsLocale", "ru");
        this.$i18n.locale = "ru";
      }
      moment.locale(this.$i18n.locale);
    },
  },
  mounted() {
    this.checkLang();
  },
};
</script>
