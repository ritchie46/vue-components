<template>
  <div class="vue-component-spreadsheet" v-bind:id="id">
  </div>
</template>

<script>
import Handsontable from 'handsontable'

export default {
  name: 'SpreadSheet',

  props: {
    hotSettings: Object,
    id: String,

  },

  data: function () {
    return {
      hot: null
    }
  },

  mounted() {
    let container = document.getElementById(this.id);
    this.hot = new Handsontable(container, this.hotSettings)

  }
}
</script>


<style src="../../node_modules/handsontable/dist/handsontable.full.css"></style>
