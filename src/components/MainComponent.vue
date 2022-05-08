<template>
  <div class="container-fluid d-flex flex-column align-items-center">
    <SiteSelect @selectGenere="search" v-model="genreSelected"/>
    <div class="container">
      <div class="row pt-5" v-if="!loader">
          <SiteDisk :disk="disc" v-for="(disc, index) in filtered" :key="index"/>
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
import state from "@/state.js";
import axios from "axios";
import SiteSelect from "@/components/SelectComponent.vue";
import SiteDisk from "@/components/DiscComponent.vue"
export default {
  nome: "SiteMain",
  components:{
      SiteDisk,
      SiteSelect
  },
  methods:{
     search() {
      console.log('Searching ...');
      console.log(this.genreSelected);
    }
  },
  computed:{
    filtered(){
       if(state.searchText) {
        return this.discs.filter(disc => {
          return disc.author.toLowerCase() == state.searchText.toLowerCase()
        })
      }else if(this.genreSelected){
        return this.discs.filter(disc => {
          return disc.genre.toLowerCase() == this.genreSelected.toLowerCase()
        })
      }
      else {
        return this.discs
      }
    },
  },
  data() {
    return {
      link: "https://flynn.boolean.careers/exercises/api/array/music",
      discs: null,
      loader: true,
      error: null,
      genreSelected:''   
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