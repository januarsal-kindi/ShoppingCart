<template>
    <div class="container">
        <h1 class="header"> Shipping-CheckOut</h1>
            <InfoDetail v-bind:info="info"></InfoDetail>
        <h1 class="header"></h1>
        <div class ="row">
            <div class="col-3">
                <span class="help-text-info">Delivary Detail</span>
            </div>
            <div class="col-6" style="text-align:left">
                <label for="dynamic-label-input"> {{shipping.deliveryServices}} - {{shipping.deliveryDay}}</label>
            </div>
        </div>
        <div class ="row">
            <div class="col-3">
                <span class="help-text-info">Delivary Price</span>
            </div>
            <div class="col-6" style="text-align:left">
                <label for="dynamic-label-input">Rp {{formatPrice(shipping.deliveryPrice)}}</label>
            </div>
        </div>
        <div class ="row">
            <div class="col-3">
                <span class="help-text-info">Service Price</span>
            </div>
            <div class="col-6" style="text-align:left">
                <label for="dynamic-label-input">Rp 2.000</label>
            </div>
        </div>
        <div class ="row">
            <div class="col-3">
                <span class="help-text-info">Total Price</span>
            </div>
            <div class="col-6" style="text-align:left">
                <label for="dynamic-label-input">Rp {{formatPrice(shipping.deliveryPrice+2000)}}</label>
            </div>
        </div>
        <div class ="row">
            <div class="col-3">
                <span class="help-text-info">pay method</span>
            </div>
            <div class="col-6" style="text-align:left">
                <label for="dynamic-label-input">{{shipping.paymentMethod}}</label>
            </div>
        </div>
               
        <div class="row" style="margin-bottom:20px">
               <button  v-on:click="showContainer(2)" class="button3">Back</button>
               <button  class="button3">finish</button>
        </div>
    </div>
</template>
<script>

import InfoDetail from "../shared/InfoDetail"

export default {
  props: ['shipping','info'],
  name: 'FinishPayment',
   components:{
      InfoDetail
  },
  data () {
    return {
  
      paymentServices:{
          wallet : true,
          bank_transfer: true,
          virtual_account : true
      } 
    }
  },
  methods:{
    showContainer: function(index) {
		this.$emit('container', index);
    },
    formatPrice: function(value) {
        let val = (value/1).toFixed(2).replace('.', ',')
        return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".")
    }
  }
}
</script>


<style>

.container {
    max-width: 100%;
    margin: 20px auto;
    padding: 1.5rem 2rem;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
}


.container label {
    font-weight: bold;
    font-size: 1em
}
.header {
    margin-bottom: 1.5rem;
    padding-bottom: 1rem;
    border-bottom: 1px solid var(--gray-lighter);
    font-size: var(--font-size-3);
    text-align: center;
}

       
.btn-group button {
    background-color: #4CAF50; /* Green background */
    border: 1px solid green; /* Green border */
    color: white; /* White text */
    padding: 10px 24px; /* Some padding */
    cursor: pointer; /* Pointer/hand icon */
    float: left; /* Float the buttons side by side */
}

.btn-group button:not(:last-child) {
    border-right: none; /* Prevent double borders */
}

/* Clear floats (clearfix hack) */
.btn-group:after {
    content: "";
    clear: both;
    display: table;
}

/* Add a background color on hover */
.btn-group button:hover {
    background-color: #3e8e41;
}

.container {
    display: block;
    position: relative;
    padding-left: 35px;
    margin-bottom: 12px;
    cursor: pointer;
    font-size: 22px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}

/* Hide the browser's default radio button */
.radiobtn input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
}
.help-text-info {
    display: block;
    margin-top: 0.5rem;
    font-size: var(--font-size-small);
}

/* Create a custom radio button */
.checkmark {
    position: absolute;
    top: 0;
    left: 0;
    height: 25px;
    width: 25px;
    background-color: #eee;
    border-radius: 50%;
}

/* On mouse-over, add a grey background color */


</style>

