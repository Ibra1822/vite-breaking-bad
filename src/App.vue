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
      axios.get(store.api).then((result) => {
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
  <MainComp />
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>
