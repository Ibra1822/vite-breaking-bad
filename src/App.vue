<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";
import axios from "axios";
import { store } from "./data/store.js";

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

    find() {},
  },
  mounted() {
    this.getApi();
  },
};
</script>

<template>
  <HeaderComp />
  {{ store.category }}
  <MainComp @search="find" />
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>
