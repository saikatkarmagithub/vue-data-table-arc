<template lang="pug">
  table
    tr
      th(v-for="(cell, headerIndex) in header")
        template(v-if="options.columns[headerIndex].sortable") {{ cell }}
          span(class="icon-arrow-up-circle" @click="sort(headerIndex, 'Descinding')")
          span(class="icon-arrow-down-circle" @click="sort(headerIndex, 'Ascending')")
        template(v-else) {{ cell }}  
    tr(v-for="(row, rowIndex) in data")
      td(v-for="(cell, colIndex) in row" @click="edit(rowIndex, colIndex)")
        template(v-if="!options.columns[colIndex].editable") {{ cell }}
        template(v-else-if="(selectedIndex[0] === rowIndex && selectedIndex[1] === colIndex)")
          input(v-model="data[rowIndex][colIndex]" :type="options.columns[colIndex].type" :ref="`input-${rowIndex}-${colIndex}`")
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
        const el = this.$refs[`input-${rowIndex}-${colIndex}`][0]
        el.focus()
        el.addEventListener('focusout', () => {
          this.selectedIndex = []
      })
          el.removeEventListener('focusout')
        })
    },
    sort(headerIndex, whichSort) {
      let temp
      console.log('start')
      console.log(this.data)
      for(let i= 0; i < this.data.length-1; i++) {
        for(let j =0; j < this.data.length-1-i; j++) {
          if(whichSort === 'Ascending') {
            if(this.data[j][headerIndex] > this.data[j+1][headerIndex]) {
              temp = this.data[j]
              this.data[j] = this.data[j+1]
              this.data[j+1] = temp
            }
          }
          else {
            if(this.data[j][headerIndex] < this.data[j+1][headerIndex]) {
              temp = this.data[j]
              this.data[j] = this.data[j+1]
              this.data[j+1] = temp
            }
          }
        }
      }
      console.log('end')
      console.log(this.data)
    },
  }
}
</script>

<style lang="sass" scoped>
</style>
