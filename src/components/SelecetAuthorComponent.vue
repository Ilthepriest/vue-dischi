<template>
  <select class="form-select w-25 h-50"
   aria-label="Default select example"
   :value="authorSelected"
   @input="$emit('input', $event.target.value)"
   @change="$emit('selectAuthor')">

      <option value="" selected>Seleziona Autore</option>
      <option>Bon Jovi</option>
      <option>Queen</option>
      <option>Sting</option>
      <option>Iron Maiden</option>
      <option>Eric Clapton</option>
      <option>Deep Purple</option>
      <option>Metallica</option>
      <option>Dave Weckl</option>
      <option>Michael Jacjson</option>
    </select>
</template>

<script>
export default {
    nome: 'SiteSelectAuthor',
    props:{
        authorSelected: String
    },
}
</script>

<style lang="scss" scoped>

</style>