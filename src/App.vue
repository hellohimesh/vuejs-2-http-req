<template>
  <div id="app">
  <input type="text" v-model="x.email">
  <input type="password" v-model="x.password">
  <button v-on:click="post(x)">submit</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {x:{
   email:"test@gmail.com",
    password : "test"
    }
    }
      },
      methods:{
        post:function(x){
          this.$http.post('https://reqres.in/api/register',x).then(function(res){
            console.log(res);
          })
        },
        get:function(){
          this.$http.get('https://reqres.in/api/users?page=2').then(function(res){
            console.log(res.data.data);
          },function(error){
            console.log(error);
          })
        }
      },
       beforeMount(){
         this.get();
       }
  }

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
