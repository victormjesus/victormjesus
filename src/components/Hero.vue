<template>
  <div class='container'>
    <div class='row'>
      <div class='hero-text col-md-6'>
        <h2 >Conheça a Plataforma Nacional</h2>
        <h6>
          A Escala de Avaliação de Ambientes 
          de Aprendizagem para a Primeira Infância (EAPI) 
          é um indicador utilizado para avaliar os ambientes 
          de aprendizagem da primeira infância a nível Nacional. 
          O EAPI já foi aplicado em mais de x cidades. Com um total de x aplicadores certificados...   
          Lorem Ipsum is simply dummy text of the printing and typesetting industry. 
        </h6>
        <Button value="Saiba Mais" color="blue" />
      </div>
      
      <div class='hero-img col-md-6'>
        <img src='../assets/img/map.png' width='500' height='500'>
      </div>

   </div>
  </div>

</template>

<script>
import Button from './Button';

export default {
  name: 'Hero',
  components: {
    Button
  }
}
</script>

<style scoped>

  .hero-text h2 {
    color: #105B9F;
    font-weight: bold;
  }

  .hero-text h6 {
    margin-bottom: 1rem;
  }

  h2,h6{
    text-align:justify;
  }

  .hero-text{
    padding: 200px 0px;
  }

  .hero-img{
    padding: 50px 0px 50px 120px;
  }
 
</style>
