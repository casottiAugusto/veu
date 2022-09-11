<template>
  <div class="app">
    <h3>Cadastro</h3>
    <small class="erro" v-show="deuerro">O campo nome esta vazio </small>
    <input
      type="text"
      name="name"
      v-model="nomeFileld"
      placeholder="Nome do infeliz"
    /><br />
    <small class="erro" v-show="deuerro">O campo descrição esta vazio </small>
    <input
      type="text"
      name="descricao"
      v-model="descricaoField"
      placeholder="Descrição do Infeliz"
    /><br />
    <small class="erro" v-show="deuerro">O idade nome esta vazio </small>
    <input
      type="number"
      name="idade"
      v-model="idadeField"
      placeholder="Idade do Infeliz"
    /><br />
     <button @click="cadastrar" class="button is-success is-small">Cadastras</button>
   
    <hr />
    <div v-for="(cliente, index) in orderCliente" :key="cliente.id">
      <h4>{{ index + 1 }}</h4>
      <Cliente :cliente="cliente" @DeletaEu="deletarUser($event)"/>
      <hr />
    </div>
  </div>
</template>

<script>
import Cliente from "./components/Cliente.vue";
//import Produto from './components/Produto.vue'
import _ from 'lodash';

export default {
  name: "App",
  data() {
    return {
      deuerro:false,
      nomeFileld: "",
      descricaoField: "",
      idadeField: 0,
      clientes: [
        {
          id: 6,
          nome: "Hcliente1",
          descricao: "Um cara legal",
          idade: 10,
        },
        {
          id: 1,
          nome: "Ccliente1",
          descricao: "Um cara legal",
          idade: 10,
        },
        {
          id: 2,
          nome: "Bcliente",
          descricao: "Um cara legal",
          idade: 10,
        },
        {
          id: 3,
          nome: "Kcliente1",
          descricao: "Um cara legal",
          idade: 10,
        },
        {
          id: 4,
          nome: "Ecliente1",
          descricao: "Um cara legal",
          idade: 10,
        },
        {
          id: 5,
          nome: "Dliente1",
          descricao: "Um cara legal",
          idade: 10,
        },
      ],
    };
  },
  components: {
    Cliente,

    //Produto
  },
  methods: {
    cadastrar: function () {
      if (
        this.nomeFileld == "" ||
        this.descricaoField == "" ||
        this.idadeField == " "
      ) {
         this.deuerro=true;
      } else{
        this.clientes.push({
          nome: this.nomeFileld,
          descricao: this.descricaoField,
          idade: this.idadeField,
          id: Date.now(),        
        });
          this.deuerro=false;
        }
      this.nomeFileld = "";
      this.descricaoField = "";
      this.idadeField = 0;
    },
    deletarUser:function ($event) {
     
      
      let id =$event.idCliente;
      let novoArry =this.clientes.filter(cliente => cliente.id != id);
      this.clientes=novoArry
      
    }
  },
  computed:{
    orderCliente: function () {
      return _.orderBy(this.clientes,['nome'],['asc'])
      
    }
  }
};
</script>

<style>
 .erro{
  color: red;

}


</style>
