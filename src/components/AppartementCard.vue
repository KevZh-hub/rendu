<template>
  <div 
    class="border m-2 p-2 flex justify-between"
    :class="disponibleStyle"
  >
    <div>
      <h1 class="text-lg font-bold">{{ AppartementName }}</h1>
    </div>
    <base-button    
      text="Voir l'offre"
      @click="addToSelection"
    >
    </base-button>
  </div>
</template>

<script>
export default {
  name: "appartement-card",
  props: ['appartement'],
  computed: {
    AppartementName(){
      if(this.appartement.name.split('.').length > 1){
        return this.appartement.name.split('.')[1]
      }
      return this.appartement.name;
    },
    isNotAvailable() {
      if(this.appartement.disponible == "Vendu"){
        return true
      }
      return false
    },
    disponibleStyle() {
      return { 
        'bg-gray-600': this.isNotAvailable, 
        'border-white': this.isNotAvailable, 
        'border-black': !this.isNotAvailable 
      }
    }
  },
  methods: {
    addToSelection() {
      this.$emit('add-appartement', this.appartement)
    }
  }
}
</script>

<style scoped>

</style>