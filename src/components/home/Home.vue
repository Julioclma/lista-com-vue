<template>
    <div class="corpo">
      <h1 class="centralizado">{{ titulo }}</h1>
  
      <input type="search" class="filtro" @input="filtro = $event.target.value" placeholder="Encontre pelo titulo">
      {{ filtro }}
      <ul class="lista-fotos">
        <li class="lista-fotos-item" v-for="foto of fotosComFiltros">
          <meu-painel :titulo="foto.titulo">
            <imagem-responsiva :url="foto.url" :titulo="foto.titulo" />
          </meu-painel>
  
        </li>
      </ul>
  
  
    </div>
  </template>
  
  <script>
  
  import Painel from '../shared/painel/Painel.vue';
  import ImagemResponsiva from '../shared/imagem-responsiva/ImagemResponsiva.vue';
  
  export default {
  
    components: {
      'meu-painel': Painel,
      'imagem-responsiva': ImagemResponsiva
    },
  
    data() {
      return {
        titulo: 'Fotografias',
  
        fotos: [
  
        ],
        filtro: ''
      }
  
    },
  
    computed: {
  
      fotosComFiltros() {
  
        if (this.filtro) {
  
          let exp = new RegExp(this.filtro.trim(), 'i');
  
          return this.fotos.filter(foto => exp.test(foto.titulo));
  
        } else {
  
          return this.fotos;
  
        }
      }
  
    },
  
    created() {
      this.$http.get('http://localhost:3000/v1/fotos')
        .then(res => res.json())
        .then(fotos => this.fotos = fotos, error => console.log(error))
    }
  
  }
  
  </script>
  
  <style>
  .corpo {
    font-family: Helvetica, sans-serif;
    width: 80%;
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
  
  .filtro {
    width: 100%;
  }
  </style>
  