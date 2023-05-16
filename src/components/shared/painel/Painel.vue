<template>
          <div class="painel">
            <div class="painel-titulo">
                {{ titulo }}
            </div>
            <slot class="painel-conteudo">
            </slot>
          </div>
  </template>
  
  <script>
  
  export default {
  
    props: ['titulo', 'url']

  }
  
  </script>
  
  <style>
  /* estilo do painel */
  .painel {
    box-shadow: 1px 1px 1px rgb(0, 0, 0);
  
    border-radius: 5px;
  }
  
  .painel .painel-titulo { 
    
    border-radius: 5px 5px 0 0;
    text-align: center;
    border: solid 1px;
    background: lightblue;
  }
  </style>
  