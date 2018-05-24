<template>
     <div class="container">
        <h1 class="header"> Shipping-CheckOut</h1>
        <InfoDetail v-bind:info="info"></InfoDetail>
        <h1 class="header"></h1>
        <div class ="row">
            <div class="col-3">
                <label for="dynamic-label-input">Jasa</label>
            </div>
            <div class="col-6">
                <div class="btn-group">
                    <button v-on:click="selectService(1)" >JNE</button>
                    <button v-on:click="selectService(2)">Go Send</button>
                    <button v-on:click="selectService(3)">Sicepat</button>
                </div>
                
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
                <span class="help-text-info">Delivary Estimate</span>
            </div>
            <div class="col-6" style="text-align:left">
                <label for="dynamic-label-input">{{shipping.deliveryDay}}</label>
            </div>
        </div>
            

            <div class="row" style="text-align:left">
               <div class="col-3">
                    <span class="help-text-info">Pay Metode</span>
                 </div>
                 <div class="col-6" style="text-align:left">
              <fieldset>
                <div v-if="paymentServices.wallet" class="radio">
                    <input type="radio" name="radio" id="check-option-1" value="wallet" checked v-model="shipping.paymentMethod"  />
                    <label for="check-option-1">Wallet</label>
                </div>
                <div v-if="paymentServices.bank_transfer" class="radio">
                    <input type="radio" name="radio" id="check-option-2" value="Bank Transfer" v-model="shipping.paymentMethod"/>
                    <label for="check-option-2">Bank Transfer</label>
                </div>
                 <div v-if="paymentServices.virtual_account" class="radio">
                    <input type="radio" name="radio" id="check-option-3" value="Virtual Account" v-model="shipping.paymentMethod"/>
                    <label for="check-option-3">Virtual Account</label>
                </div>
            </fieldset>
            </div>
            </div>
            <div class="row" style="margin-bottom:20px">
               <button  v-on:click="showContainer(1)" class="button3">Back</button>
                <button  v-on:click="showContainer(3)" class="button3">Next</button>
            </div>
    </div>
</template>
<script>

import InfoDetail from "../shared/InfoDetail"

export default {
  props: ['shipping','info'],
  name: 'Shipping',
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
    formatPrice(value) {
        let val = (value/1).toFixed(2).replace('.', ',')
        return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".")
    },
    selectService: function(index) {
        if (index === 1){
           this.shipping.deliveryServices = 'JNE';
           this.shipping.deliveryDay = '2 day';
           this.shipping.deliveryPrice =  15000;

           //payment service available
           this.paymentServices.wallet =true;
           this.paymentServices.virtual_account =true;
           this.paymentServices.bank_transfer =false;



        }else if (index === 2){
           this.shipping.deliveryServices = 'Go Send';
           this.shipping.deliveryDay = 'half day';
           this.shipping.deliveryPrice =  35000;

             this.paymentServices.wallet =true;
           this.paymentServices.virtual_account =false;
           this.paymentServices.bank_transfer =false;

           t

        }else if (index === 3){
           this.shipping.deliveryServices = 'Sicepat';
           this.shipping.deliveryDay = '1 day';
           this.shipping.deliveryPrice =  10000;

           this.paymentServices.wallet =true;
           this.paymentServices.virtual_account =false;
           this.paymentServices.bank_transfer =true;

        }
    },
     
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

