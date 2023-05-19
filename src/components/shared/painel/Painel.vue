<template>
  <div class="painel">
    <div class="painel-titulo" @click="visivel = !visivel">

      {{ titulo }}
    </div>
    <transition name="painel-fade">
      <div class="painel-conteudo" v-show="visivel">
        <slot>
        </slot>
      </div>
    </transition>
  </div>
</template>
  
<script>

export default {

  props: ['titulo'],

  data() {
    return {
      visivel: true
    }
  }


}

</script>
  
<style scoped>
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

* {
  box-shadow: 5px 5px 10px black;
}

.painel-fade-enter, .painel-fade-leave-active{
opacity: 0;
}

.painel-fade-enter-active, .painel-fade-leave-active{
transition: .4s;
}
</style>
  