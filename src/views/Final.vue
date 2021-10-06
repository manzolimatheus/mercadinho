<template>
  <div class="container">
      <FormFinal :preco="preco"/>
  </div>
</template>

<script>

import FormFinal from "@/components/FormFinal.vue";

export default {
    name: 'Final',
    components:{
        FormFinal
    },
    created(){
        this.preco = this.$route.params
    }
}
</script>

<style>

</style>