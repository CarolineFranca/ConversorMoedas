<template>
    <div class="container">

        <div class="title">
            <h2> Conversor  <hr>   </h2>                    
        </div>
        
    <div class="box1"> 
            <p> Moeda Brasileira (BRL) </p>

        <div>
        <input type="number" placeholder="Valor" v-model="moedaA_value">
            <hr>
            <input type="number" placeholder="Cotação" v-model="cotacao_value"> 
        </div>         
    </div>    
    
     <div class="button">
        <button @click="limpar"> Limpar </button>     

        <button @click="converter()"> Converter </button>     
    </div>    
    
     <span class="icon"> $ </span>

     <div class="box2">
         <p> USD </p>

        <span> {{moedaB_value}} </span>
     </div>

     

    </div>
</template>

<script>
export default {
    props: ["moedaA", "moedaB"],
    data(){
        return{

            moedaA_value: "",  //inserção
            cotacao_value: "",     //cotação
            moedaB_value: "", //resultado
            id: 1,
            cambio: "",
        }
    },
        
    methods: {

        converter(){    
            if(this.moedaA_value == 0 || this.cotacao_value == 0){
                this.moedaB_value = (" ")
            }else {
                var total = this.moedaA_value / this.cotacao_value;
                this.moedaB_value = ("$ "+ total.toFixed(2));
                console.log(this.moedaB_value)               
          }
        },

        limpar(){
            this.moedaA_value = " ";
            this.cotacao_value = " ";
            this.moedaB_value = " ";
        }
    }
}

</script>


<style scoped>
    
    *{
        font-family: 'Girassol', cursive, Arial;
    }
 .container{
     display: grid;
     grid-template-columns: 35fr 15fr 35fr;
     grid-template-rows: 20fr 50fr 20fr;
     width: 99vw;
     height: 99vh;
 }

 .title{
     grid-column: 2;
     display: flex;
     justify-content: center;
     align-items: center;
     font-size: 2em;
 }

 .title > h2 >  hr {
     border: none;
     height: 3px;
     width: 50%;
     margin: auto;
     background-color: #d44000;
 }

.box1{
    grid-row: 2;
    grid-column: 1;    
    height: 8em;
    width: 20em;
    margin: auto;
    border: 2px #2978b5 solid;
    border-radius: 10px;    
    padding-bottom: 0.5em;
    z-index: 1;
}

.box1 > p {
    font-size: 25px;
    display: flex;
    justify-content: center;
    margin-top: 2px;
    padding-bottom: 3px;
    border-bottom: 2px solid #2978b5;
}

.box1 > div >  input {
    font-size: 1.3em;
    padding: 2px;
    border: none;
    width: 100%;
    padding-top: 0.5em;    
    text-align: center;
}

input:focus, select:focus {
    outline: 0;
}

.button{
    grid-column: 1;
    grid-row: 2;
    display: flex;
    justify-content: center;
    align-items: flex-end;
    z-index: 0;
}

.button > button{
    width: 10em;
    height: 3.5em;
    text-align: center;
    border: 2px #2978b5 solid;
    border-radius: 10px;
    margin: 2em;
    cursor: pointer;
    letter-spacing: 2px;
    font-size: 0.8em;
    font-family: Arial, Helvetica, sans-serif;
}

.button > button:first-child{
    border: 2px  #2978b5 solid;
    background-color: #2978b500;
    color: #2978b5;
    font-weight: 700;
}

.button > button:first-child:hover{
    border: 2px  #810000 solid;
    background-color: #810000;
    color: #ffffff;
}

.button > button:last-child{
    border: 2px  #2978b5 solid;
    background-color: #2978b5;
    color: #ffffff;
}

.button > button:last-child:hover{
    border: 2px  #d44000 solid;
    background-color: #d44000;
    color: #ffffff;
}

.icon{
    grid-row: 2;
    grid-column: 2;
    display: grid;
    place-items: center;
    font-size: 12em;
    color: #d44000;
}

.icon:hover{
    color: #d44000a2;
    cursor: pointer;
}

.box2{
    grid-row: 2;
    grid-column: 3;    
    height: 9em;
    width: 20em;
    margin: auto;
    border: 2px #2978b5 solid;
    border-radius: 10px;  
}

.box2 > p {
    font-size: 25px;
    display: flex;
    justify-content: center;
    font-family: 'Girassol', cursive, Arial;
    margin-top: 2px;
    padding-bottom: 3px;
    border-bottom: 2px solid #2978b5;
}

.box2 > span{
    font-size: 3em;
    height: 12vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

@media (max-width: 900px){
    .title{
        font-size: 20px;
    }
    .icon{
        font-size: 100px;
    }
    .box1, .box2{
        width:  16em;
        height: 8em;
    }
    .button{
        width:  18em;
        margin-left: auto;
        margin-right: auto;
    }
}

@media (max-width: 600px) {
    .container{
        grid-template-rows: 50fr 50fr;
        grid-template-columns: 80fr 10fr;
    }    
    .box1{
        grid-row: 1;
        margin: auto;
    }
    .button{
        grid-row: 1;
        margin-left: auto;
    }
    .box2{
        grid-row: 2;
        grid-column: 1;
        margin: auto;
    } 
    .icon, .title{
        display: none;
    }      
}
</style>