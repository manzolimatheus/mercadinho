<template>
  <div class="home">
    <Destaque/>
    <div class="container">
    <h1 data-aos="fade-right">Conheça nossos serviços</h1>
    <div class="cards">
      <Card
        nome="Açougue"
        img="https://images.unsplash.com/photo-1615937662601-4724eceda00f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80"
        alt="Açougue"
      />
      <Card 
      nome="Padaria" 
      img="https://images.unsplash.com/photo-1509440159596-0249088772ff?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=872&q=80"
      alt="Padaria"
      />
      <Card 
      nome="Hortifruti"
      img="https://images.unsplash.com/photo-1573246123716-6b1782bfc499?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=765&q=80"
      alt="Hortifruti" 
      />
    </div>
    </div>
  </div>
</template>

<script>
import Destaque from "@/components/Destaque.vue";
import Card from "@/components/Card.vue";

export default {
  name: "Home",
  components: {
    Destaque,
    Card,
  },
};
</script>

<style>
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.container{
  padding: 3%;
}

.container h1{
  text-align: center;
}

@media (max-width: 768px){
  .cards{
    overflow-x: scroll;
  }
}

</style>
