<template>
<div :class="{'cliente':!isPrimiun,'clientePrime': isPrimiun}">
<h4>Nome:{{processarNome }}</h4>
<hr>
<p>Descrição:{{cliente.descricao}}</p>
<hr>  
<p > Idade:{{cliente.idade}}</p>
   
<button @click="mudarcor">Mudar Cor!!</button>
<button @click="emitirEcentoDeletar">Deletar!!!!</button>

<hr>
</div>
</template>
<script>
export default {
  data(){
    return{
      isPrimiun:false
      
     
    }
  },
  props:{
  
    cliente: Object,
    
  },
  methods:{
    mudarcor: function ($event) {
      console.log($event)
     this.isPrimiun= !this.isPrimiun
    },
    emitirEcentoDeletar: function(){
      console.log("Emitir evento")
      this.$emit("DeletaEu",{idCliente:this.cliente.id})
    }
  },
  computed:{
    processarNome:function(){
      return this.cliente.nome.toUpperCase();

    }
  }
  
}
</script>
<style scoped>
  .cliente{
    background-color: #ece5e3;
    border:1px black solid;
    font-size: 24px;
    padding: 3%;
    margin-top: 2%;
    width: 750px;
    height: 350px;

}
  .clientePrime{
    background-color: whitesmoke;
    font-size: 24px;
    padding: 3%;
    margin-top: 2%;
    border:1px black solid;
    width: 750px;
    height: 350px;


  }

</style>