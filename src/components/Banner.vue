<template>
    <div class="main-banner">
        <h1>Burger Banner</h1>
    </div>
</template>
<script>
export default{
    name:'Banner'
}
</script>
<style scoped>
.main-banner{
    background-image: url('../../public/img/burger.jpg');
    background-position: 0 -250px;
    background-size: cover;
    height: 500px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
}
.main-banner h1{
    color: #fff;
    text-align: center;
    font-size: 60px;
    background-color: #222;
    padding: 20px 40px;
    border-radius: 8px;
}
</style>