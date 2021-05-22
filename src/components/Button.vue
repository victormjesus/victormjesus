<!--
|---------------------------------------------
| Button Component 
|---------------------------------------------
| @usage Import the component and use <Button value='Button Text' section='Section Name'/>
| Sections main colors: 
|   main => #18A0FB
|   boas_praticas => #41B3A3
|   materiais_documentos => #EB7071
|   certificacao => #F498C0
|   dados =>  #0d9f9f;
|   outline: dados #0d9f9f w/ border
-->

<template>
  <button v-if="!isOutline" :class="'button grow ' + section">
    {{ value }}
  </button>
  <button
    v-else
    :class="['button-outline ' + section, { 'shadow-button': hasShadow }]"
  >
    <div v-if="!isReverse">
      <i v-if="hasIcon" :class="'fas fa-' + iconName + ' mr-1'"></i>
      <span class="m-0">{{ value }}</span>
    </div>

    <div v-else>
      <span class="m-0">{{ value }}</span>
      <i v-if="hasIcon" :class="'fas fa-' + iconName + ' ml-1'"></i>
    </div>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    section: String,
    value: String,
    isOutline: Boolean,
    hasIcon: Boolean,
    hasShadow: Boolean,
    iconName: String,
    isReverse: Boolean
  },
};
</script>

<style scoped>
/* BOTAO OUTLINE */

.button-outline {
  border-radius: 4px;
  padding: 0.4rem 0.8rem;
  font-weight: bold;
  cursor: pointer;
  outline: none;
  transition: all ease-in-out 0.2s;
}

.shadow-button {
  -webkit-box-shadow: 10px 10px 5px -1px rgba(0, 0, 0, 0.15);
  -moz-box-shadow: 10px 10px 5px -1px rgba(0, 0, 0, 0.15);
  box-shadow: 6px 6px 5px -1px rgba(0, 0, 0, 0.15);
}

/* PADRAO DE CORES PARA BOTOES OUTLINE */
.dados-outline {
  border: 1px solid #0d9f9f;
  color: #0d9f9f;
  background-color: white;
}

.dados-outline:hover {
  color: white;
  background-color: #0d9f9f;
}

.painel-outline {
  border: 1px solid #0d9f9f;
  color: #0d9f9f;
  background-color: white;
}

.painel-outline:hover {
  color: white;
  background-color: #0d9f9f;
}

.instituicao-cadastrar {
  border: 1px solid #676bd6;
  color: #676bd6;
  background-color: white;
}

.instituicao-cadastrar:hover {
  color: white;
  background-color: #676bd6;
}

.instituicao-campo {
  border: 1px solid #7647ac;
  color: #7647ac;
  background-color: white;
}

.instituicao-campo:hover {
  color: white;
  background-color: #7647ac;
}

.instituicao-aplicacoes {
  border: 1px solid #ffac30;
  color: #ffac30;
  background-color: white;
}

.instituicao-aplicacoes:hover {
  color: white;
  background-color: #ffac30;
}

/* ----------------- BOTAO NORMAL ----------------- */

.button {
  color: white;
  max-height: 2.5rem;
  width: auto;
  font-size: 14px;
  font-weight: bold;
  text-transform: uppercase;
  padding: 0.6rem 0.6rem 0.6rem 0.6rem;
  outline: none;
  border: none;
  cursor: pointer;
}

.main {
  border-radius: 6px;
  background-color: #18a0fb;
  box-shadow: -1px 2px 10px 2px rgba(24, 160, 251, 0.3);
  transition: all ease-in-out 0.26s;
}

.main:hover {
  background-color: #1a85cc;
  box-shadow: -1px 2px 10px 2px rgba(61, 138, 189, 0.384);
}

.boas-praticas {
  border-radius: 20px;
  background-color: #41b3a3;
  transition: all ease-in-out 0.26s;
}

.boas-praticas:hover {
  background-color: #339c8e;
}

.materiais-documentos {
  border-radius: 20px;
  background-color: #eb7071;
  transition: all ease-in-out 0.26s;
}

.materiais-documentos:hover {
  background-color: #ac4242;
}

.certificacao {
  border-radius: 20px;
  background-color: #f498c0;
  transition: all ease-in-out 0.26s;
}

.certificacao:hover {
  background-color: #c57396;
}

.dados {
  border-radius: 20px;
  background-color: #0d9f9f;
  transition: all ease-in-out 0.26s;
}

.dados:hover {
  background-color: #0db3b3;
}
</style>
