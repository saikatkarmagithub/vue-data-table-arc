<template lang="pug">
  table
    tr
      th(v-for="cell in header") {{ cell }}
    tr(v-for="(row, rowIndex) in data")
      td(v-for="(cell, colIndex) in row" @click="edit(rowIndex, colIndex)")
        template(v-if="!options.editable") {{ cell }}
        template(v-else-if="(selectedIndex[0] === rowIndex && selectedIndex[1] === colIndex)")
          template(v-if="options.datatype === 'text'")
            input(v-model="data[rowIndex][colIndex]" type="text" :ref="`input-${rowIndex}-${colIndex}`")
          template(v-else)
            input(v-model="data[rowIndex][colIndex]" type="number" :ref="`input-${rowIndex}-${colIndex}`")
        template(v-else) {{ cell }}  
</template>

<script>
export default {
  data () {
    return {
      selectedIndex: [],
    };
  },
  props: {
    header: Array,
    data: Array,
    options: Object
  },
  methods: {
    edit(rowIndex, colIndex) {
      this.selectedIndex = [rowIndex, colIndex]
      this.$nextTick(() => {
        this.$refs[`input-${rowIndex}-${colIndex}`][0].focus()
      })
    }
  }
}
</script>

<style lang="sass" scoped>
</style>
