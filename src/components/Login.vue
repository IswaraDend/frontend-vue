<template>
    <div class="row">
        <div class="col-sm-4">

            <h2 align="center"> Login </h2>

              <form @submit.prevent="LoginData">
                  <div class="form=group" align="left">
                    <label>Email</label>
                    <input type="email" v-model="student.email" class="form-control" placeholder="Email">
                  </div>

                  <div class="form=group" align="left">
                    <label>Password</label>
                    <input type="password" v-model="student.password" class="form-control" placeholder="Password">
                  </div>

                  <button type="submit" class="btn btn-primary">Login</button>
              </form>
        </div>
    </div>

</template>
  
<script>
import Vue from 'vue';
import axios from 'axios';

Vue.use(axios)
export default {
    name: 'Register',
    data () {
        return {
            result: {},
            student:{
                email: '',
                password: ''
            }
        }
    },
    created(){

    },
    mounted() {
        console.log("mounted() called.......");
    },
    methods: {
        LoginData()
        {
            axios.post("http://127.0.0.1:8000/api/login", this.student)
            .then(
                ({data})=>{
                    console.log(data);
                    try {
                      if (data.status === true) {
                        alert("Login Succesfully");
                        this.$router.push({name: 'HelloWorld'})
                      } else {
                        alert("Login failed")
                      }
                        
                    } catch (err) {
                        alert("error, please try again");
                    }
                }
            )
        }
    }
}

</script>
  