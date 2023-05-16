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
        {
          url: 'https://www.vocenaneve.com.br/app/uploads/2022/07/Denali-1.jpg',
          titulo: 'Montanha no Gelo'
        },
        {
          url: 'https://dynamic-media-cdn.tripadvisor.com/media/photo-o/09/2b/28/01/pedra-da-gavea.jpg?w=500&h=-1&s=1',
          titulo: 'Rio de Janeiro Montanha Incrivel'
        }

      ]
    }
  }

}
</script>

<style>
img {
  width: 350px;
  height: 250px;
}
</style>
