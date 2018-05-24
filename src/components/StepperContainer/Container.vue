<template>
     <div class="container">
        <form>
            <h1>Information - CheckOut</h1>

            <div class="row">
                <div style="margin-top:3%;  display: inline-block;" class="col-3">
                    <div class="checkbox">
                        <input type="checkbox" name="checkbox" id="check-option-1" value="1" checked />
                        <label for="check-option-1">Send As Dropshipper</label>
                    </div>
                </div>
                 <div class="col-3">
                    <p class="has-dynamic-label">
                        <input  v-bind:class="[isSubmit === nameshipper.status ? 'valid' : 'invalid']" v-model="info.nameshipper" type="text" id="dynamic-label-input"  placeholder="Name dropshipper" required>
                        <label for="dynamic-label-input">Name dropshipper</label>
                        <span  class="help-text">{{nameshipper.message}}</span>
                    </p>
                </div>
                 <div class="col-3">
                    <p class="has-dynamic-label">
                        <input  v-bind:class="[isSubmit === phonenumbershipper.status ? 'valid' : 'invalid']" max="999999999"  v-model="info.phonenumbershipper"  type="number" id="dynamic-label-input"  placeholder="phone number" required>
                        <label for="dynamic-label-input">phone number</label>
                        <span  class="help-text">{{phonenumbershipper.message}}</span>
                    </p>
                </div>
            </div>

            <div class ="row">
                <div class="col-6">
                    <p class="has-dynamic-label">
                        <input  v-bind:class="[isSubmit === name.status ? 'valid' : 'invalid']" v-model="infoship.name"  type="text" id="dynamic-label-input"  placeholder="Name" required>
                        <label for="dynamic-label-input">Name</label>
                        <span class="help-text">{{name.message}}</span>
                    </p>
                </div>
            </div>

            <div class ="row">
                <div class="col-6">
                    <p class="has-dynamic-label">
                        <input  v-bind:class="[isSubmit === phonenumber.status ? 'valid' : 'invalid']" class="valid"  maxlength="12"  v-model="infoship.phonenumber"  type="number" id="dynamic-label-input"  placeholder="PhoneNumber" required>
                        <label for="dynamic-label-input">PhoneNumber</label>
                        <span  class="help-text">{{phonenumber.message}}</span>
                    </p>
                </div>
            </div>
            <div class ="row">
                <div class="col-6">
                    <p class="has-dynamic-label">
                        <textarea  v-bind:class="[isSubmit === address.status ? 'valid' : 'invalid']" v-model="info.address" type="text" id="dynamic-label-input"  placeholder="Address" required></textarea>
                        <label for="dynamic-label-input">Address</label>
                        <span   class="help-text"> {{address.message}}</span>
                    </p>
                </div>
            </div>
            <div class ="row">
                <div class="col-6">
                     <p class="has-dynamic-label">
                        <label   for="valid-email">Email</label>
                        <input v-bind:class="[isSubmit === email.status ? 'valid' : 'invalid']" class="valid" v-model="infoship.email"  type="email" id="valid-email"  required>
                        <span class="help-text"> {{email.message}}</span>
                    </p>
                </div>
            </div>
        </form>
        <div class="row" style="margin-bottom:20px">
                <button  v-on:click="showContainer(2)" class="button3">Next</button>
        </div>
    </div>
</template>
<script>


export default {
  props: ['info'],
  name: 'Container',
  
  data () {
    return {
        isSubmit : false,
        infoship:this.info,
        name:{
            status: false,
            message: ""
        },
        nameshipper:{
            status: false,
            message: ""
        },
        phonenumbershipper:{
            status: false,
            message: ""
        },
        phonenumber:{
            status: false,
            message: ""
        },
        address:{
            status: false,
            message: ""
        },
        email:{
            status: false,
            message: ""
        },

    }
  },
   methods:{
    showContainer: function(index) {
        this.isSubmit= true;

       if(this.checkForm()){
		    this.$emit('container', index);
       }

    },
    checkForm : function(){

        let result = true;

        if(this.infoship.name !== ""){
            this.name.status == true;
            this.name.message = "";
        }else{
            this.name.status == false;
            this.name.message == "name is requerid";
            result = false;
        } 


        if (this.infoship.nameshipper !== ""){
            this.nameshipper.status = true;
            this.nameshipper.message = "";
        }else {
             this.nameshipper.status = false;
             this.nameshipper.message = "name shipper is requered";
            result = false;

        } 

        if (this.infoship.phonenumbershipper !== ""){
            this.phonenumbershipper.status = true
            this.phonenumbershipper.message = "";


        }else{
            this.phonenumbershipper.status = false;
            this.phonenumbershipper.message = "phonenumber shipper is requered";
            result = false;
        }

        if (this.infoship.phonenumber !== ""){
            this.phonenumber.status = true
            this.phonenumber.message = "";

        }else{
            this.phonenumber.status = false;
            this.phonenumber.message = "phonenumber shipper is requered";
            result = false;
        }


        if (this.infoship.address !== ""){
            this.address.status = true
            this.address.message = "";

        }else{
            this.address.status == false;
            this.address.message = "address shipper is requered";
            result = false;
        }

        if (this.infoship.email !== ""){

            if(this.validateemail(this.infoship.email)){
                this.email.status = true
                this.email.message = "";
            }else{
                this.email.status = false;
                this.email.message = "Invalid Forma email";
                result = false;
            }
         
        }else{
            this.email.status = false;
            this.email.message = "address shipper is requered";
            result = false;
        }

        return result;
        
    },validateemail:function(email){
        var re = /^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return re.test(email);
    }
  }
}
</script>


<style>
  :root {
            --color-primary: #2eec96;
            --selection-color: #abffd9;
            --unitless-max-font-size: 18;
        }

        

        form {
            max-width: 100%;
            margin: 20px auto;
            padding: 1.5rem 2rem;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
        }

        form h1 {
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid var(--gray-lighter);
            font-size: var(--font-size-3);
            text-align: center;
        }

        input {
            background-repeat: no-repeat;
            background-position: right 1rem center;
            background-size: 0.75rem;
        }
        textarea {
            background-repeat: no-repeat;
            background-position: right 1rem center;
            background-size: 0.75rem;
        }

        .help-text {
            display: block;
            margin-top: 0.5rem;
            color: red;
            font-size: var(--font-size-small);
        }
     

        input:placeholder-shown + label {
            opacity: 0;
            transform: translateY(1rem);
        }
        textarea:placeholder-shown + label {
            opacity: 0;
            transform: translateY(1rem);
        }

        .has-dynamic-label {
            position: relative;
            padding-top: 1.5rem;
        }

        .has-dynamic-label label {
            position: absolute;
            top: 0;
            font-size: var(--font-size-small);
            opacity: 1;
            transform: translateY(0);
            transition: all 0.2s ease-out;
        }

      

        input:optional + .help-text::before {
            content: '*Optional';
        }

        input:read-only {
            border-color: var(--gray-lighter) !important;
            color: var(--gray);
            cursor: not-allowed;
        }

        .valid {
            border-color: #2eec96;
            background-image: url("data:image/svg+xml,%3Csvg width='45px' height='34px' viewBox='0 0 45 34' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd'%3E%3Cg transform='translate%28-56.000000, -59.000000%29' fill='%232EEC96'%3E%3Cpolygon points='70.1468531 85.8671329 97.013986 59 100.58042 62.5664336 70.1468531 93 56 78.8531469 59.5664336 75.2867133'%3E%3C/polygon%3E%3C/g%3E%3C/g%3E%3C/svg%3E%0A");
        }

        .invalid {
            border-color: red;
            background-image: url("data:image/svg+xml,%3Csvg width='30px' height='30px' viewBox='0 0 30 30' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd'%3E%3Cg transform='translate%28-128.000000, -59.000000%29' fill='%23F44336'%3E%3Cpolygon points='157.848404 61.9920213 145.980053 73.8603723 157.848404 85.7287234 154.856383 88.7207447 142.988032 76.8523936 131.119681 88.7207447 128.12766 85.7287234 139.996011 73.8603723 128.12766 61.9920213 131.119681 59 142.988032 70.8683511 154.856383 59'%3E%3C/polygon%3E%3C/g%3E%3C/g%3E%3C/svg%3E%0A");
        }

        .invalid:focus {
            border-color: var(--color-error);
        }

        .invalid + .help-text {
            color: var(--color-error);
        }

      

        input:out-of-range + .help-text::before {
            content: 'Out of range';
        }

        input[type='checkbox'] + label {
            user-select: none;
        }
</style>

