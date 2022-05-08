<template>
  <select class="form-select w-25"
   aria-label="Default select example"
   :value="genreSelected"
   @input="$emit('input', $event.target.value)"
   @change="$emit('selectGenere')">

      <option value="" selected>Seleziona genere</option>
      <option>Rock</option>
      <option>Pop</option>
      <option>Jazz</option>
      <option>Metal</option>
    </select>
</template>

<script>
export default {
    nome: 'SiteSelect',
    props:{
        genreSelected: String
    },
}
</script>

<style lang="scss" scoped>

</style>