<template>
    <div class="message">
        <p class="texto">Pedido enviado com sucesso</p>
        <button class="botao">x</button>
    </div>
</template>
<script>
export default{
    name:'Message'
}
</script>
<style scoped>
.message{
    display: flex;
    align-items: center;
    justify-content: center;
    border: 4px solid yellow;
}
.texto{
    font-size: 14px;
    color:white;
    font-family: helvetica;
    font-weight: 900;
}
</style>