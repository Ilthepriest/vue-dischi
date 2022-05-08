<template>
  <div class="container-fluid">
      <div class="row d-flex justify-content-between align-items-center">
          <img src="@/assets/img/logo-small.svg" alt="">
          <SiteSelectAuthor @selectAuthor="search" v-model="authorSelected"/>
      </div>
  </div>
</template>

<script>
import SiteSelectAuthor from "@/components/SelecetAuthorComponent.vue";
import state from "@/state.js"
export default {
    nome: 'SiteHeader',
    components:{
        SiteSelectAuthor
    },
      methods: {
    search() {
      state.searchText = this.authorSelected;
    },
  },
  data() {
    return {
      searchText: "",
      authorSelected: ""
    };
  },
}
</script>

<style lang="scss" scoped>
.row{
    background-color: $bg-header;
    height: 100px;
    img{
        width: 70px;
        margin-left: 20px;
    }
}
</style>