<template>
  <div class="col d-flex justify-content-center gy-3">
    <div class="card bg_card p-3 pb-4 text-center">
      <img :src="disk.poster" alt="" />
      <h5 class="mt-2">{{ disk.author }}</h5>
      <p>{{ disk.author }}</p>
      <p>{{ disk.year }}</p>
    </div>
  </div>
</template>

<script>
export default {
    nome: 'SiteDisk',
    props: {
        disk: Object
    }
};
</script>

<style lang="scss" >
  p {
    color: $secondary-text;
  }
  .bg_card {
    background-color: $bg-card !important;
  }
  h5 {
    color: white;
  }
  img {
    width: 200px;
    aspect-ratio: 1 / 1;
  }
</style>