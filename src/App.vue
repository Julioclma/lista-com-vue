<template>
  <div>
    <h1>{{ titulo }}</h1>
    <ul>
      <li v-for="foto of fotos">
        <div>
          <h3>{{ foto.titulo }}</h3>
          <img :src="foto.url" :alt="foto.titulo" />
        </div>
      </li>
    </ul>


  </div>
</template>

<script>





export default {

  data() {
    return {
      titulo: 'Fotografias',

      fotos: [
      
      ]
    }
    
  },
  
  created(){
this.$http.get('http://localhost:3000/v1/fotos')
.then(res => res.json())
.then(fotos => this.fotos = fotos)
//  console.log(fotos);
  }

}

</script>

<style>
img {
  width: 350px;
  height: 250px;
}
</style>
