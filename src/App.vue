<template>
  <nav-bar
    @change-component="changeSelectedComponent"
  >
  </nav-bar>
  
  <keep-alive include="appartement-view">
    <component 
      :is="selectedComponent"
      v-bind="currentProps"
      @child-event="selectionUpdate"
    >
    </component>
  </keep-alive>
  
</template>

<script>

import AppartementView from './components/AppartementView.vue'
import SelectionList from './components/SelectionList.vue'
import NavBar from './components/navigation/NavBar.vue'

export default {
  name: 'App',
  components: {
    AppartementView,
    SelectionList,
    NavBar
  },
  data() {
    return {
      selectedComponent: 'appartement-view',
      appartementSelection: []
    }
  },
  computed: {
    currentProps() {
      if(this.selectedComponent == "selection-list"){
        return { selection: this.appartementSelection }
      }
      return false
    },
  },
  methods: {
    changeSelectedComponent(value) {
      this.selectedComponent = value
    },
    selectionUpdate(value) {
      this.appartementSelection.push(value)
    }
  }
}
</script>

<style>
 
</style>
