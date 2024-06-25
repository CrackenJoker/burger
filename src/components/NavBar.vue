<template>
    <div>
      <div class="navBar">
        <router-link to="/" id="logo-url">
            <img :src="logo" :alt="alt" id="logo">
        </router-link>
        <router-link to="/">Fazer Pedido</router-link>
        <router-link to="/pedidos">Pedidos</router-link>
      </div>
    </div>
</template>
<script>
export default{
    name:"NavBar",
    props:[
        "logo",
        "alt"
    ]
}
</script>
<style scoped>
.navBar{
    display: flex;
    justify-content: flex-end;
    padding: 15px 50px;
    background-color: #222;
    border-bottom: 4px solid #111;
    align-items: center;
}
.navBar #logo-url{
    margin: auto;
    margin-left: 0;
}

#logo{
    width: 40px;
    height: 40px;
}
.navBar a{
    color: #FCBA03;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
}
.navBar a:hover{
    color: #fff;
}
</style>