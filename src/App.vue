<template>
  <Header/>
  <FormularioNovoMedicamento @cadastrar="adicionarMedicamento"/>
  <div class="container">
   <cardMedicamento 
    v-for="medicamento in listaMedicamentos"
    :key="medicamento.id"
     @favoritar="favoritarMedicamento" 
     :nome="medicamento.nome" 
     :laboratorio="medicamento.laboratorio" 
     :preco="medicamento.preco" 
     :id="medicamento.id"/>
  </div>
  
</template>

<script>
  import Header from "./components/Header.vue"
  import FormularioNovoMedicamento from "./components/FormularioNovoMedicamento/index.vue"
  import cardMedicamento from "./components/cardMedicamento/index.vue"

  export default {
    components: {
      Header,
      FormularioNovoMedicamento,
      cardMedicamento
    },
    data() {
      return {
        listaMedicamentos: []
      }
    },
    methods: {
      adicionarMedicamento(nome, laboratorio, preco) {
        if(nome == '' || laboratorio == '' || preco == 0) {
          alert('Preencha todos os dados!')
          return
        } 

        const novoMedicamento = {
          id: this.listaMedicamentos.length + 1,
          nome: nome,
          laboratorio: laboratorio,
          preco: preco,
          favorito: false
        }

        this.listaMedicamentos.push(novoMedicamento)
      },
      favoritarMedicamento(id) {
        this.listaMedicamentos = this.listaMedicamentos.map(item => {
          if(item.id == id){
            item.favorito = !item.favorito
          }
         console.log(item)
          return item
        })
      }
    }
  }
</script>

<style scoped>
  .container {
    display: flex;
    flex-wrap: wrap;
    width: 100vw;
    padding: 1em;
  }
</style>
