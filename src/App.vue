<template>
  <div id="app">
    <stepper v-bind:indexContainer="container" v-on:container="showContainer"></stepper>
      <!-- <div class="container-header">
        <hello-world></hello-world>
    </div> -->
    <information  v-bind:info="info"   v-on:container="showContainer" v-if="container === 1"></information>
    <Shipping v-bind:shipping="shipping" v-bind:info="info" v-on:container="showContainer" v-if="container === 2"></Shipping>
    <FinishPayment v-bind:shipping="shipping" v-bind:info="info" v-on:container="showContainer" v-if="container === 3"></FinishPayment>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Information from './components/StepperContainer/Container'
import Shipping from './components/StepperContainer/Shipping'
import FinishPayment from './components/StepperContainer/FinishPayment'
import Stepper from './components/Stepper'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Stepper,
    Information,
    Shipping,
    FinishPayment
  },
  data () {
    return {
      info:{
        nameshipper : '',
        phonenumbershipper:'',
        name:'',
        phonenumber:'',
        address:'',
        email: '',
      },
       shipping:{
        deliveryServices : '',
        deliveryDay:'',
        deliveryPrice:'',
        servicePrice:'',
        paymentMethod:'wallet',
      },
      container: 1
    }
  },
  methods: {
    showContainer(indexCon) {

      if(indexCon == 2 && this.info.nameshipper !== ''){
        this.container = indexCon;
      }else if (indexCon == 3 && this.shipping.deliveryServices !== ''){
        this.container = indexCon;
      }else if (indexCon ==1){
        this.container = indexCon;

      }
      
    },
   
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%
}
</style>
