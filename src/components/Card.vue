<template>
  <div class="card" data-aos="flip-left">
    <h3 class="truncate">
      {{ nome }}
    </h3>
    <span v-show="preco">R${{ preco }}</span>
    <div class="imagem">
      <img :src="img" :alt="alt" />
    </div>
    <br />
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    nome: String,
    img: String,
    alt: String,
    preco: Number,
  },
};
</script>

<style scoped>
.card {
  background-color: white;
  border-radius: 10px;
  height: fit-content;
  padding: 3%;
}

.card h3 {
  border-left: 5px solid rgb(75, 223, 142);
  padding-left: 2%;
}

.imagem{
width: 100%;
height: 300px;
}

.card img {
  width: 100%;
  height: 100%;
  border-radius: 10px;
  object-fit: cover;
  filter: brightness(0.9);
}

.truncate {
  width: 300px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>