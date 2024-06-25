<template>
  <NavBar :logo="logo" :alt="nome_logo"/>
  <router-view/>
  <Footer/>
</template>
<script>
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'
export default{
  components:{
    NavBar,
    Footer
  },
  data(){
    return{
      logo:'/img/logo.png',
      name_logo:'Make Your Burger'
    }
  }

}
</script>
<style>
*{
  font-family: helvetica;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.main-container{
  margin: 50px;
  min-height: 250px;
}
h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color:#222;
}
</style>
