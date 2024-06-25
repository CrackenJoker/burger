<template>
    <div class="main-Form-Burger">
        <Message/>
        <form id="burger-form" @submit="createBurger">
            
            <div class="input-container">
                <label for="nome">Nome cliente</label>
                <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digite seu nome"/>
            </div>
            
            <div class="input-container">
                <label for="pao">Selecione o pão</label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione o tipo de pão</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
                </select>
            </div>
            
            <div class="input-container">
                <label for="carne">Selecione a carne</label>
                <select name="carne" id="carne" v-model="carne">
                    <option value="">Selecione o tipo de carne</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                </select>
            </div>

            <div class="input-container" id="check-container">
                <label for="opcionais" id="opcionais-title">Selecione os opcionais</label>
                <div class="check-main-container" v-for="opcao in opcionaisData" :key="opcao.id">
                    <input type="checkbox" name="opcionais" v-model="opcional" :value="opcao.tipo">
                    <span>{{ opcao.tipo }}</span>
                </div>

            </div>

            <div class="input-container">
                <input type="submit" value="Criar meu Burger" class="btn-submit">
            </div>


        </form>
    </div>
</template>
<script>
import Message from './Message.vue'
export default{
    name:'BurgerForm',
    components:{
        Message
    },
    data(){
        return{
            paes:null,
            carnes:null,
            opcionaisData:null,
            nome:null,
            pao:null,
            carne:null,
            opcional:[],
            msg:null
        }
    },
    methods:{
        async getIgredientes(){
            const req = await fetch("http://localhost:3000/ingredientes")
            const data = await req.json()
            //console.log(data)
            this.paes = data.paes;
            this.carnes = data.carnes;
            this.opcionaisData = data.opcionais;
        },
        async createBurger(e){
            e.preventDefault()
            const data = {
                nome:this.nome,
                pao:this.pao,
                carne:this.carne,
                opcao:Array.from(this.opcional),
                status:"Solicitado"
            }
            const dataJson = JSON.stringify(data)
            const req = await fetch("http://localhost:3000/burgers",{
                method:"POST",
                headers:{"Content-Type":"application/json"},
                body:dataJson
            })
            //const res = await req.json()
            
        }
        
    },
    mounted() {
            this.getIgredientes()
        }
}
</script>
<style scoped>
    #burger-form{
        max-width: 400px;
        margin: 0 auto;
    }
    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }
    label{
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #FCBA03;
    }
    input,select{
        padding: 5px 10px;
        width: 300px;
    }
    .check-main-container{
        flex-direction: row;
        flex-wrap: wrap;
    }
    #opcionais-title{
        width: 100%;
    }
    #check-container{
        display: flex;
        align-items: flex-start;
        width: 40%;
        margin-bottom: 20px;
    }
    .check-main-container input,
    .check-main-container span{
        width: auto;
    }
    .check-main-container span{
        margin-left: 8px;
        font-weight: bold;
    }
    .btn-submit{
        background-color: #222;
        color: #FCBA03;
        border: 2px solid #222;
        font-weight: bold;
        font-size: 16px;
        padding: 10px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }
    .btn-submit:hover{
        background-color: transparent;
        color: #222;

    }
</style>