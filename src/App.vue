<template>
    <div>
      <!-- <h1>{{ message }}</h1> -->
      <Login 
      v-if='!isLogin'
      :changeIsLogin='changeIsLogin'
      :baseUrl = 'baseUrl'
      ></Login>
      <Home :baseUrl="baseUrl" v-if='isLogin' :changeIsLogin='changeIsLogin' ></Home>
    </div>
</template>

<script>
import Login from './view/Login.vue'
import Home from './view/Home.vue'
export default {
  data() {
    return {
      message: 'Hello world',
      isLogin: false,
      baseUrl: 'https://nu-tech-test-alkindi.herokuapp.com/'
    };
  },
  components: {
      Login,
      Home
  },
  methods : {
      changeIsLogin(value){
          this.isLogin = value
      }
  },
  created(){
      if(localStorage.access_token){
          this.isLogin = true
      }else{
          this.isLogin = false
      }
  }
};
</script>