<template>
  <div class="border border-black text-center m-4 p-4">
    Selection : {{ selection.length }}
    <span v-if="numberSelection">appartement</span>
    <span v-else>appartements</span>

    <ul>
      <li v-for="appartements in selection" :key="appartements.adresse">{{ appartements.adresse }}</li>
    </ul>

  </div>
  
</template>

<script>
export default {
  name: "selection-box",
  props: ['selection'],
  computed: {
    numberSelection(){
      if(this.selection.length < 2){
        return true
      }
      return false
    }
  }

}
</script>

<style>

</style>