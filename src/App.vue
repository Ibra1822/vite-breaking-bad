<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";
import axios from "axios";
import { store } from "./data/store.js";
import { includeBooleanAttr } from "@vue/shared";

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    getApi() {
      store.isLoaded = false;
      axios
        .get(store.api, {
          params: { category: store.category },
        })
        .then((result) => {
          store.array = result.data;
          store.isLoaded = true;
        });
    },
  },
  mounted() {
    this.getApi();
  },
};
</script>

<template>
  <HeaderComp />
  <MainComp @search="getApi" />
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>
