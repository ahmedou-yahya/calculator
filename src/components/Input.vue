<template>
  <input type="number" v-model="input" @change="onInputChange">
</template>

<script>
export default {
  name: 'Input',
  data() {
    return {
      input: 0,
    }
  },
  methods:{
    onInputChange(){
      this.$emit('input-change', this.input)
    }
  }
}
</script>

<style scoped>

</style>