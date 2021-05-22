<!--
|---------------------------------------------
| Navbar Component 
|---------------------------------------------
| @usage Import the component and use, no params
| Main Navbar component
-->

<template>
  <div>
    <!-- <ModalLateral ref="ModalLogin" component="Login" title="Entrar" />
    <ModalLateral ref="ModalSignUp" component="SignUp" title="Cadastre-se" /> -->

    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <router-link to="/"
        ><img id="logo" src="../assets/img/App/Navbar/logo-navbar.png"
      /></router-link>

      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item dropdown">
            <a
              @click="showDropdownMenuBoasPraticas"
              class="nav-link nav-item dropdown-toggle"
              href="#"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Boas Práticas</a
            >
            <DropdownMenu ref="DropdownMenuBoasPraticas" menuDropdown="boas_praticas"/>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <a class="dropdown-item" href="#">Vídeos</a>
              <a class="dropdown-item" href="#">Acervo de Práticas</a>
              <a class="dropdown-item" href="#">Acervo de Projetos</a>
            </div>
          </li>
          <li class="nav-item dropdown">
            <a
              @click="showDropdownMenuMateriais"
              class="nav-link nav-item dropdown-toggle"
              href="#"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Materiais e Documentos</a
            >
            <DropdownMenu ref="DropdownMenuMateriais" menuDropdown="materiais"/>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <a class="dropdown-item" href="#">O que é?</a>
              <a class="dropdown-item" href="#">Materiais e Documentos</a>
            </div>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              href="http://certificacao.monitoramentoeibv.fearp.usp.br"
              target="_blank"
            >
              Certificação</a
            >
          </li>
          <li class="nav-item dropdown">
            <a
              @click="showDropdownMenuDados"
              class="nav-link nav-item dropdown-toggle"
              href="#"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Dados</a
            >
            <DropdownMenu ref="DropdownMenuDados" menuDropdown="dados"/>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <a class="dropdown-item" href="/dados/gerenciar/instituicao">Gerenciar Instituições</a>
              <a class="dropdown-item" href="/dados/gerenciar/grupos">Grupos de Pesquisa</a>
              <a class="dropdown-item" href="/dados/exportardevolutiva">Exportar Devolutiva</a>
              <a class="dropdown-item" href="/dados/baixardadosnacionais">Baixar Dados Nacionais</a>
            </div>
          </li>
        </ul>

        <ul v-if='!logged' class="navbar-nav mr-auto">
          <li class="nav-item">
            <Button
              class="btn"
              @click="openSignUp"
              section="main"
              value="Obtenha sua Certificação"
            />
          </li>

          <li class="nav-item">
            <p id="ou">Ou</p>
          </li>

          <li class="nav-item">
            <p @click="openLogin" id="acesse">Acesse</p>
          </li>
        </ul>

        <ul v-else> Olá, Nome do Usuário <button @click='logout'>Sair</button></ul>
      </div>
    </nav>
  </div>
</template>

<script>
import Button from "./Button";
import DropdownMenu from "./DropdownMenu";


export default {
  name: "Navbar",
  props:{
    logged: Boolean
  },
  components: {
    Button,
    DropdownMenu
  },
  methods: {
    openLogin() {
      this.$refs.ModalLogin.showModalLateral();
    },
    closeLogin() {
      this.$refs.ModalLogin.closeModalLateral();
    },
    openSignUp() {
      this.$refs.ModalSignUp.showModalLateral();
    },
    closeSignUp() {
      this.$refs.ModalSignUp.closeModalLateral();
    },
    showDropdownMenuBoasPraticas() {
      this.$refs.DropdownMenuBoasPraticas.getScreenSizeforOverlay();
      this.$refs.DropdownMenuBoasPraticas.showDropdownMenu();
    },
    showDropdownMenuMateriais() {
      this.$refs.DropdownMenuMateriais.getScreenSizeforOverlay();
      this.$refs.DropdownMenuMateriais.showDropdownMenu();
    },
    showDropdownMenuDados() {
      this.$refs.DropdownMenuDados.getScreenSizeforOverlay();
      this.$refs.DropdownMenuDados.showDropdownMenu();
    },
    logout(){
      localStorage.removeItem('accessToken')
    }
  },
};
</script>

<style scoped>
/*
 |-----------------------------------------------------
 |--ESTILIZANDO A PRÓPRIA NAVBAR (TAMANHO HORIZONTAL,
 |--ITENS DO MENU, ETC)
 |-----------------------------------------------------
 */
.navbar {
  -webkit-box-shadow: 0px 10px 38px -12px rgba(96, 133, 236, 0.425);
  -moz-box-shadow: 0px 10px 38px -12px rgba(96, 133, 236, 0.425);
  box-shadow: 0px 10px 38px -12px rgba(96, 133, 236, 0.425);
}

#logo {
  max-height: 3.8rem;
  /* width: auto;
    cursor: pointer; */
  margin: 0rem 3rem;
}

#logo2 {
  max-height: 3.8rem;
  width: auto;
  cursor: pointer;
}

ul {
  font-size: 16px;
  text-transform: uppercase;
  color: #766565;
  font-weight: bold;
  list-style: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0;
}

ul li {
  margin: 0 1rem 0 0;
  cursor: pointer;
}

#ou {
  font-size: 16px;
  font-weight: bold;
  color: #635a5a;
  text-transform: uppercase;
  margin-bottom: 0;
  cursor: default;
}

#acesse {
  font-size: 16px;
  font-weight: bold;
  color: #18a0fb;
  text-transform: uppercase;
  text-decoration: underline;
  cursor: pointer;
  margin-bottom: 0;
  transition: all ease-in-out 0.26s;
}

.arrow {
  display: inline-block;
  border-top: 6px solid #766565;
  border-left: 4px solid transparent;
  border-right: 4px solid transparent;
  margin-left: 5px;
  vertical-align: middle;
}

.nav-item {
  text-align: center;
}

.dropdown-menu {
  margin: 0rem 0rem 0.8rem 0rem;
  border: none;
  padding: 0.05rem;
  background-color: #e0e0e0;
}

.dropdown-menu .dropdown-item {
  background-color: #f8f7f7;
  padding: 0.4rem;
  font-size: 0.8rem;
  color: rgba(0, 0, 0, 0.5);
  text-align: center;
  text-transform: none;
  text-align: center;
}

.dropdown-menu .dropdown-item:hover {
  background-color: #e0e0e0;
  color: rgba(0, 0, 0, 0.7);
}

.navbar-light .navbar-nav .nav-link {
  transition: all ease-in-out 0.2s;
}

/*-----------------------------------------------------*/

/*
 |-----------------------------------------------------
 |--ADICIONANDO PSEUDO-CLASSE :FOCUS PARA EXIBIR DROPDOWN
 |-----------------------------------------------------
 */
#acesse:hover {
  color: #1a85cc;
}
/*-----------------------------------------------------*/

/*
 |-----------------------------------------------------
 |--ADICIONANDO @MEDIA QUERIES
 |-----------------------------------------------------
*/
@media screen and (max-width: 991px) {
  #ou {
    margin: 0.4rem 0rem;
  }
}

@media screen and (min-width: 992px) {
  .dropdown-menu {
    display: none;
  }
}

@media (min-width: 992px) {
  .navbar-expand-lg .navbar-nav {
    flex-wrap: wrap;
    justify-content: space-evenly;
  }
}

.navbar-light .navbar-nav .active>.nav-link, .navbar-light .navbar-nav .nav-link.active, .navbar-light .navbar-nav .nav-link.show, .navbar-light .navbar-nav .show>.nav-link {
  color: rgb(0 0 0 / 60%);
}

/*-----------------------------------------------------*/
</style>
