<template>
  <div class="corpo">
    <h1 class="centralizado">{{ titulo }}</h1>
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto of fotos">
 <meu-painel :titulo="foto.titulo">
   <img :src="foto.url" :alt="foto.titulo" />
 </meu-painel>
         
      </li>
    </ul>


  </div>
</template>

<script>

import Painel from './components/shared/painel/Painel.vue';

export default {

  components: {
    'meu-painel': Painel
  },

  data() {
    return {
      titulo: 'Fotografias',

      fotos: [

      ]
    }

  },

  created() {
    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, error => console.log(error))
    //  console.log(fotos);
  }

}

</script>

<style>
.corpo {
  font-family: Helvetica, sans-serif;
  width: 96%;
  margin: 0 auto;
}

.centralizado {
  text-align: center;
}

.lista-fotos {
  display: flex;
  flex-wrap: wrap;
}

.lista-fotos-item {
  margin: 0 5px;
  list-style: none;
}


</style>
