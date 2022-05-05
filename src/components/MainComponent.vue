<template>
  <div class="container-fluid">
    <div class="container">
      <div class="row pt-5" v-if="!loader">
          <SiteDisk :disk="disc" v-for="(disc, index) in discs" :key="index"/>
      </div>
      <div v-else>
        <div class="text-center ">
          <div class="spinner-border text-light" role="status">
            <span class="visually-hidden">Loading...</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SiteDisk from "@/components/DiscComponent.vue"
export default {
  nome: "SiteMain",
  components:{
      SiteDisk,
  },
  data() {
    return {
      link: "https://flynn.boolean.careers/exercises/api/array/music",
      discs: null,
      loader: true,
      error: null
    };
  },
  mounted() {
    console.log(axios);
    axios
      .get(this.link)
      .then((response) => {
        this.discs = response.data.response;
        this.loader = false;
      })
      .catch((error) => {
        console.log(error);
        this.error = `Scusa c'è un errore ${this.error}`
      });
  },
};
</script>
<style lang="scss" scoped>
.container-fluid {
  height: calc(100vh - 100px);
  overflow: auto;
  background-color: $bg-color;
}
</style>