<template>
    <form @submit.prevent="handleSubmit">
        <label>name</label>
        <input type="text"  v-model="name">

        <div v-if="!$v.name.required" class="error" >Name is required</div>
        <!-- <div v-if="$v.name.$error">Name field has an error.</div> -->

         <!-- <div class="error" v-if="!$v.name.minLength">Name must have at least {{$v.name.$params.minLength.min}} letters.</div> -->
<!-- 
        <label>email</label>
        <input type="email"  v-model="email">

        <div class="error" v-if="!$v.email.required">email is required</div>
        <div class="error" v-if="!$v.email.minLength">email must have at least {{$v.email.$params.minLength.min}} letters.</div>

        <label>phone</label>
        <input type="text"  v-model="phone">

        <div class="error" v-if="!$v.phone.required">phone is required</div>
        <div class="error" v-if="!$v.phone.minLength">phone must have at least {{$v.phone.$params.minLength.min}} letters.</div>

        <label>address</label>
        <input type="text"  v-model="address"> -->

        <button class="button" type="submit" :disabled="submitStatus === 'PENDING'">Submit!</button>
        <!-- <p class="" v-if="submitStatus === 'OK'">Thanks for your submission!</p>
        <p class="" v-if="submitStatus === 'ERROR'">Please fill the form correctly.</p>
        <p class="" v-if="submitStatus === 'PENDING'">Sending...</p> -->
    </form>

  

</template>

<script>

    const { validationMixin, default: Vuelidate } = require('vuelidate')
    const { required, minLength } = require('vuelidate/lib/validators')

    // const { validationMixin, default: Vuelidate } = require('vuelidate')
    // const { required, minLength } = require('vuelidate/lib/validators')

    export default{

        name: 'SignupForm',
        props:[],
        data(){
            return {
                name:'',
                email:'',
                phone:'',
                address:'',
            }
        },
        validations:{
            name: {
                required,
                minLength: minLength(4)
            },
            email: {
                required,
                minLength: minLength(5),
            },
            phone: {
                required,
                minLength: minLength(10),
            },
            address: {
                required,
                minLength: minLength(4),
            },
        },
        methods:{
            handleSubmit(){
                // console.log(this.v$);
                // this.v$.$validate() // checks all inputs
                // if (!this.v$.$error) {
                //     // if ANY fail validation
                //     alert('Form successfully submitted.');
                // } else {
                //     alert('Form failed validation');
                // }
            },
        },

    }
    
</script>

<style>
  form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }

  button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin:auto;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
  }
  .submit {
    text-align: center;
  }
  .error {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }
</style>