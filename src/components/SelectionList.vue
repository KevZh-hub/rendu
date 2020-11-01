<template>
  <div class="container w-4/5 mx-auto mt-4">
    <h1 class="text-lg font-bold">Ma sélection</h1>

    <div v-if="selection.length == 0">
      <p>Aucun appartement sélectionné</p>
    </div>
    <div v-else>
      <div
        v-for="appartement in selection"
        :key="appartement.adresse" 
        class="border border-black my-4 p-2"
      >
        <h3>{{ appartement.adresse }} ({{ appartement.prix }})</h3>
        <span>Dimension : {{ appartement.dimension }}</span>
        <img :src="require('../assets/img/' + appartement.photo)" alt="">
      </div>
    </div>

  </div>
  
</template>

<script>
export default {
  name: "selection-list",
  props: ['selection'],
}
</script>

<style>

</style>