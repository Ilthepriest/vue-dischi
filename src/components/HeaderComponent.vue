<template>
  <div class="container-fluid">
      <div class="row">
          <img src="@/assets/img/logo-small.svg" alt="">
      </div>
  </div>
</template>

<script>
export default {
    nome: 'SiteHeader'
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