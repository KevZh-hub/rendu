<template>

  <img alt="Logo appartement" src="../assets/img/logo.png">
  <div class="flex">
    <div class="w-1/5">
      <selection-box
        :selection="selection"
      >
      </selection-box>
    </div>
    

    <div class="w-4/5 mt-2">
      <Appartement-card 
        v-for="(appartement, index) in annonces.appartements"
        :key="index"
        :appartement="appartement"
        @add-Appartement="addAppartementToSelection"
        >
      </Appartement-card>
    </div>
    

  </div>
    
</template>

<script>
import annoncesData from '../data/appartements.json'
import AppartementCard from './AppartementCard.vue'
import SelectionBox from './SelectionBox.vue'

export default {
  name: "appartement-view",
  components: {
    AppartementCard,
    SelectionBox
  },
  data() {
    return {
      annonces: annoncesData,
      selection: []
    }
  },
  methods: {
    addAppartementToSelection(appartement){
      this.selection.push(appartement)
      this.$emit('child-event', appartement)
    }
  }
}
</script>

<style scoped>

</style>