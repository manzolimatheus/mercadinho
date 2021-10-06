<template>
  <div class="destaque">
    <div>
      <h1>Preço <span id="destaque-frase">BAIXO</span> que cabe no seu bolso!</h1>
      <hr>
      <p>Trazendo qualidade e confiança para sua mesa desde 2019.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Destaque",
  data() {
    return {};
  },
};
</script>

<style>
.destaque {
  background: linear-gradient(#00000080, rgba(0, 0, 0, 0.7)),
    url("https://images.unsplash.com/photo-1540340061722-9293d5163008?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=871&q=80");
  background-attachment: fixed;
  background-size: cover;
  background-position: center;
  height: 400px;
  width: 100%;
  display: grid;
  justify-content: center;
  align-items: center;
  color: white;
}

#destaque-frase{
  color: #24a84c;
}

.destaque p{
  text-align: center;
  color: #63ec91;
}
</style>