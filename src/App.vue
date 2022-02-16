<template>
  <div class="container">
    <div class="row">
      <Input @input-change="updateInput1"/>
    </div>
    <div class="row">
      <select  name="operator" id="" v-model="operator">
      <option  value="+" :selected="operator">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    </div>
    <div class="row">
      <Input @input-change="updateInput2"/>
    </div>
    <div class="row">=</div>
    <div>{{result}}</div>
  </div>
</template>


<script>
import Input from "@/components/Input.vue"
export default {
  name: 'App',
  components: {
    Input,
  },
  data() {
    return {
      firstOperator: 0,
      operator: "+",
      secondOperator: 0,
    }
  },
  methods: {
    updateInput1(val){
      this.firstOperator = val;
    },
    updateInput2(val){
      this.secondOperator = val;
    }
  },
  computed: {
    result(){
      let result = 0;
      switch(this.operator){
        case '+':
          result = this.firstOperator + this.secondOperator;
          break;
        case '-':
          result = this.firstOperator - this.secondOperator;
          break;
        case '*':
          result = this.firstOperator * this.secondOperator;
          break;
        case '/':
          if(this.secondOperator===0){
            return "You can't divide by zero"
          }
          result = this.firstOperator / this.secondOperator;
      }
      return result;
    }
  },
}
</script>

<style scoped>

.container{
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 100px;
  padding: 100px;
  background-color: #BBE6D6;
  border-radius: 5px;
}
</style>

