<template>

<div class="">
   <div class="bg-gray-400 border-spacing-1 m-32">
    <h1 class="text-2xl text-red-600 text-center">Login Page</h1>
    <p>email<input class ="border border-gray-400 block px-4 py-1 w-1/4 focus:border-teal-500 rounded-lg" type="email" v-model="email" /></p>
    <p>password <input class ="border border-gray-400 block px-4 py-1 w-1/4 rounded focus:outline-none focus:border-teal-500" type="password" v-model="password"/></p>
    <button @click="login" class="bg-blue-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-full m-6"> login</button>
   </div>
</div>


</template>


<script>
import axios from "axios"
export default{
    name:"login",
    data(){
        return{
            email:"",
            password:""

        }
    },
    methods:{
        async login(){
            let result=await axios.get(
                `http://localhost:3000/users?email=${this.email}&password=${this.password}`
            

            );
            console.log(this.email)
           let {email,password}=result
           console.log(email)
            if(result.status==200&& result.data.length>0){
                this.$router.push({name:"item"})
            }
            else{
                alert("please enter correct email and password")
            }
            //console.log(result)

            }
            // console.log(this.email,this.password)

    }
}




</script>