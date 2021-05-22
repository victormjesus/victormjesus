<!--
|---------------------------------------------
| DropdownMenu Component 
|---------------------------------------------
| @usage Import the component and use, no params
| A Dropdown Menu to the main Navbar
-->

<template>  
    <div>
        <!-- OVERLAY PARA TODOS DROPDOWNMENU-->
        <div v-if="screenSize > 991" @click="closeDropdownMenu" class="overlay-invisible" :class="{'overlay-visible': !isActiveDropdownMenu}"></div>
        
        <!-------------- VERSAO DESKTOP ----------------->
        
        <!-- BOAS PRATICAS -->
        <!-- DROPDOWN MAIOR E PADRÃO CASO CAIBA NA TELA -->
        <div v-if="getScreenSize() > 1500 && menu == 'boas_praticas'" class="container popup-menu mt-3" :class="{'popup-menu-visible': !isActiveDropdownMenu}">
            <svg class="triangulo-1" width="36" height="33" viewBox="0 0 36 33" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.6699 2.5C15.5944 -0.833332 20.4056 -0.833334 22.3301 2.5L35.3205 25C37.245 28.3333 34.8394 32.5 30.9904 32.5H5.00962C1.16062 32.5 -1.24501 28.3333 0.679492 25L13.6699 2.5Z" fill="white"/>
            </svg>
            <div class="row">
                <div class="col-md-8">
                    <div class="row box-md">

                        <div class="col-md-2 pl-4 icone-dropdown">
                            <img src="../assets/img/App/Navbar/icone-video.png" alt="">
                        </div>
                        <div class="col-md-10 info-dropdown">
                            <h1 class="secao-titulo-dropdown">Vídeos</h1>
                            <p class="secao-texto-dropdown">Conheça todos os vídeos referentes a boas práticas.</p>
                        </div>

                    </div>
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown">
                            <img src="../assets/img/App/Navbar/icone-acervo.png" alt="">
                        </div>
                        <div class="col-md-10 info-dropdown dropdown-icone-vertical">
                            <h1 class="secao-titulo-dropdown">Acervo de práticas</h1>
                            <p class="secao-texto-dropdown">Conheça todos as  boas práticas relacionadas a escola.</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="row box-bg">
                        <div class="col-md-12 dropdown-vertical">
                            <div class="row icone-dropdown-vertical">
                                <img src="../assets/img/App/Navbar/icone-projeto.png" alt="">
                            </div>
                            <div class="row info-dropdown-vertical">
                                <h1 class="secao-titulo-dropdown">Acervo de projetos</h1>
                                <p class="secao-texto-dropdown text-center">Conheça todos os projetos relacionados a educação infantil.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- MATERIAIS -->
        <!-- DROPDOWN MAIOR E PADRÃO CASO CAIBA NA TELA -->
        <div v-if="getScreenSize() > 1500 && menu == 'materiais'" class="container popup-menu popup-menu-small-short mt-3" :class="{'popup-menu-visible': !isActiveDropdownMenu}">
            <svg class="triangulo-1" width="36" height="33" viewBox="0 0 36 33" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.6699 2.5C15.5944 -0.833332 20.4056 -0.833334 22.3301 2.5L35.3205 25C37.245 28.3333 34.8394 32.5 30.9904 32.5H5.00962C1.16062 32.5 -1.24501 28.3333 0.679492 25L13.6699 2.5Z" fill="white"/>
            </svg>
            <div class="row">
                <div class="col-md-12 pl-0 pr-0">
                    <div class="row box-md">

                        <div class="col-md-2 icone-dropdown pl-0 pr-0">
                            <img src="../assets/img/App/Navbar/icone-oquee.png" alt="">
                        </div>
                        <div class="col-md-10 info-dropdown pl-0">
                            <h1 class="secao-titulo-dropdown">O que é?</h1>
                            <p class="secao-texto-dropdown">Entenda a seção de Materiais e Documentos.</p>
                        </div>

                    </div>
                    <div class="row box-md">
                        <div class="col-md-2 icone-dropdown pl-0 pr-0">
                            <img src="../assets/img/App/Navbar/icone-acervo.png" alt="">
                        </div>
                        <div class="col-md-10 info-dropdown pl-0">
                            <h1 class="secao-titulo-dropdown">Materiais e Documentos</h1>
                            <p class="secao-texto-dropdown">Acesse os materiais e documentos e estude para a certificação.</p>
                        </div>
                    </div>
                </div>
            </div> 
        </div>

        <!-- DADOS -->
        <!-- DROPDOWN MAIOR E PADRÃO CASO CAIBA NA TELA -->
        <div v-if="getScreenSize() > 1500 && menu == 'dados'" class="container popup-menu popup-menu-largest-dados mt-3" :class="{'popup-menu-visible': !isActiveDropdownMenu}">
            <svg class="triangulo-1" width="36" height="33" viewBox="0 0 36 33" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.6699 2.5C15.5944 -0.833332 20.4056 -0.833334 22.3301 2.5L35.3205 25C37.245 28.3333 34.8394 32.5 30.9904 32.5H5.00962C1.16062 32.5 -1.24501 28.3333 0.679492 25L13.6699 2.5Z" fill="white"/>
            </svg>
            <div class="row">
                <div class="col-md-6 pr-0">
                    <router-link to="/dados/gerenciar/instituicao" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-gerenciar.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Gerenciar Instituições</h1>
                            <p class="secao-texto-dropdown">Crie, edite ou visualize equipes de pesquisa.</p>
                        </div>
                    </div>
                    </router-link>
                    <router-link to="/dados/gerenciar/grupos" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-lupa.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Grupos de Pesquisa</h1>
                            <p class="secao-texto-dropdown">Crie, edite ou visualize suas instituições.</p>
                        </div>
                    </div>
                    </router-link>
                </div>
                <div class="col-md-6">
                    <router-link to="/dados/exportardevolutiva" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md-ml-0">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-exportar.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Exportar Devolutiva</h1>
                            <p class="secao-texto-dropdown">Gere uma devolutiva a partir de dados externos. Saiba Mais.</p>
                        </div>
                    </div>
                    </router-link>
                    <router-link to="/dados/baixardadosnacionais" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md-ml-0">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-mapa.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Baixar Dados Nacionais</h1>
                            <p class="secao-texto-dropdown">Baixe a base de dados nacional coletadas  pela nossa equipe.</p>
                        </div>
                    </div>
                    </router-link>
                </div>
            </div>    
        </div>

        <!------------- TABLET ------------>

        <!-- BOAS PRATICAS -->
        <!-- DROPDOWN MENOR E COMPACTO PARA CABER EM TELAS TABLET -->
        <div v-if="getScreenSize() > 991 && getScreenSize() < 1500 && menu == 'boas_praticas'" class="container popup-menu popup-menu-small mt-3" :class="{'popup-menu-visible': !isActiveDropdownMenu}">
            <svg class="triangulo-1" width="36" height="33" viewBox="0 0 36 33" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.6699 2.5C15.5944 -0.833332 20.4056 -0.833334 22.3301 2.5L35.3205 25C37.245 28.3333 34.8394 32.5 30.9904 32.5H5.00962C1.16062 32.5 -1.24501 28.3333 0.679492 25L13.6699 2.5Z" fill="white"/>
            </svg>
            <div class="row">
                <div class="col-md-12 pl-0 pr-0">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-video.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Vídeos</h1>
                            <p class="secao-texto-dropdown">Conheça todos os vídeos referentes a boas práticas.</p>
                        </div>
                    </div>
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-acervo.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Acervo de práticas</h1>
                            <p class="secao-texto-dropdown">Conheça todos as  boas práticas relacionadas a escola.</p>
                        </div>
                    </div>
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-projeto.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Acervo de projetos</h1>
                            <p class="secao-texto-dropdown">Conheça todos os projetos relacionados a educação infantil.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- MATERIAIS -->
        <!-- DROPDOWN MENOR E COMPACTO PARA CABER EM TELAS TABLET -->
        <div v-if="getScreenSize() > 991 && getScreenSize() < 1500 && menu == 'materiais'" class="container popup-menu popup-menu-small-materiais mt-3" :class="{'popup-menu-visible': !isActiveDropdownMenu}">
            <svg class="triangulo-1" width="36" height="33" viewBox="0 0 36 33" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.6699 2.5C15.5944 -0.833332 20.4056 -0.833334 22.3301 2.5L35.3205 25C37.245 28.3333 34.8394 32.5 30.9904 32.5H5.00962C1.16062 32.5 -1.24501 28.3333 0.679492 25L13.6699 2.5Z" fill="white"/>
            </svg>
            <div class="row">
                <div class="col-md-12 pl-0 pr-0">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-oquee.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">O que é?</h1>
                            <p class="secao-texto-dropdown">Entenda a seção de Materiais e Documentos.</p>
                        </div>
                    </div>
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-acervo.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Materiais e Documentos</h1>
                            <p class="secao-texto-dropdown">Acesse os materiais e documentos e estude para a certificação.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- DADOS -->
        <!-- DROPDOWN MENOR E COMPACTO PARA CABER EM TELAS TABLET -->
         <div v-if="getScreenSize() > 991 && getScreenSize() < 1500 && menu == 'dados'" class="container popup-menu popup-menu-highest-dados mt-3" :class="{'popup-menu-visible': !isActiveDropdownMenu}">
            <svg class="triangulo-1" width="36" height="33" viewBox="0 0 36 33" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.6699 2.5C15.5944 -0.833332 20.4056 -0.833334 22.3301 2.5L35.3205 25C37.245 28.3333 34.8394 32.5 30.9904 32.5H5.00962C1.16062 32.5 -1.24501 28.3333 0.679492 25L13.6699 2.5Z" fill="white"/>
            </svg>
            <div class="row">
                <div class="col-md-12 pl-0 pr-0">
                    <router-link to="/dados/gerenciar/instituicao" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-gerenciar.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Gerenciar Instituições</h1>
                            <p class="secao-texto-dropdown">Crie, edite ou visualize equipes de pesquisa.</p>
                        </div>
                    </div>
                    </router-link>
                    <router-link to="/dados/gerenciar/grupos" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-lupa.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Grupos de Pesquisa</h1>
                            <p class="secao-texto-dropdown">Crie, edite ou visualize suas instituições.</p>
                        </div>
                    </div>
                    </router-link>
                    <router-link to="/dados/exportardevolutiva" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-exportar.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Exportar Devolutiva</h1>
                            <p class="secao-texto-dropdown">Gere uma devolutiva a partir de dados externos. Saiba Mais.</p>
                        </div>
                    </div>
                    </router-link>
                    <router-link to="/dados/baixardadosnacionais" class="btn-router-link" @click="closeDropdownMenu">
                    <div class="row box-md">
                        <div class="col-md-2 pl-4 icone-dropdown pr-0">
                            <img src="../assets/img/App/Navbar/icone-mapa.png" alt="">
                        </div>
                        <div class="col-md-10 pl-4 info-dropdown pr-2">
                            <h1 class="secao-titulo-dropdown">Baixar Dados Nacionais</h1>
                            <p class="secao-texto-dropdown">Baixe a base de dados nacional coletadas  pela nossa equipe.</p>
                        </div>
                    </div>
                    </router-link>
                </div>
            </div>  
        </div>
    </div>
</template>

<script>
export default {
    name: 'DropdownMenu',
    data () {
        return {
            screenSize: Number,
            isActiveDropdownMenu: true,
            menu: this.menuDropdown
        }
    },
    props: {
        menuDropdown: String
    },
    methods: {
        showDropdownMenu: function() {
            this.isActiveDropdownMenu = false
        },
        closeDropdownMenu: function() {
            this.isActiveDropdownMenu = true
        },
        getScreenSize: function() {
            return window.innerWidth
        },
        getScreenSizeforOverlay: function() {
            this.screenSize = window.innerWidth
        }
    }
}
</script>

<style scoped>
/*
 |-----------------------------------------------------
 |--ADICIONANDO OVERLAY INVISIVEL 0 DE OPACITY
 |-----------------------------------------------------
 */

.overlay-invisible {
    position: fixed;
    top: 0; right: 0; bottom: 0; left: 0;
    background-color: rgba(22, 22, 22, 0.0);
    z-index: 2;
    transition: all ease-in-out 0.3s;
    opacity: 0;
    pointer-events: none;
}

.overlay-visible {
    opacity: 1;
    pointer-events: all;
    cursor: default;
}

/*-----------------------------------------------------*/

/*
 |-----------------------------------------------------
 |--RETIRANDO PADDINGS E MARGINS DAS CLASSES BOOTSTRAP
 |--DOS COMPONENTES QUE SERÃO USADOS NO DROPDOWN
 |-----------------------------------------------------
 */
.container,
.container .row,
.container .row .col-md-6,
.container .row .col-md-8,
.container .row .col-md-4 {
    padding: 0;
    margin: 0;
}
/*-----------------------------------------------------*/

/*
 |-----------------------------------------------------
 |--ESTILIZANDO O DROPDOWN DAS BOAS PRÁTICAS DO NAVBAR
 |-----------------------------------------------------
 */
.popup-menu {
    opacity: 0;
    height: 16.25rem;
    width: 30rem;
    position: absolute;
    background-color: white;
    border-radius: 0.563rem;
    z-index: 2;
    cursor: default;
    transition: all 0.4s ease;
    pointer-events: none;
    box-shadow: 1px 1px 8px -1px rgba(0, 0, 0, 0.25);
}

.popup-menu-small {
    height: 24rem;
    width: 18rem;
}

.popup-menu-small-materiais {
    height: 16.2rem;
    width: 18rem;
}

.popup-menu-highest-dados {
    height: 31.4rem;
    width: 18rem;
}

.popup-menu-small-short {
    height: 16.2rem;
    width: 24rem;
}

.popup-menu-largest-dados {
    height: 16.2rem;
    width: 34rem;
}

.popup-menu-visible {
    opacity: 1;
    pointer-events: all;
}

.box-md {
    background-color: #F5F5F5;
    height: 6.25rem;
    width: calc(100% -1.25rem);
    border-radius: 0.563rem;
    margin: 1.25rem 1.25rem 1.25rem 1.25rem !important;
    cursor: pointer;
}

.box-md-ml-0 {
    background-color: #F5F5F5;
    height: 6.25rem;
    width: calc(100% -1.25rem);
    border-radius: 0.563rem;
    margin: 1.25rem 1.25rem 1.25rem 0 !important;
    cursor: pointer;
}

.box-bg {
    background-color: #F5F5F5;
    height: 13.75rem;
    width: calc(100% -1.25rem);
    border-radius: 9px;
    margin: 1.25rem 1.25rem 1.25rem 0rem !important;
    cursor: pointer;
}

.triangulo-1 {
    position: absolute;
    left: 30px;
    top: -18px;
}

.icone-dropdown {
    display: flex;
    align-items: center;
    justify-content: center;
}

.info-dropdown {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-direction: column;
}

.secao-titulo-dropdown{
    font-size: 1rem;
    font-weight: 800;
    color: #655D5D;
    text-transform: none;
    margin-bottom: 0.2rem;
}

.secao-texto-dropdown{
    font-size: 0.8rem;
    text-align: left;
    text-transform: none;
    color: #878787;
    margin-bottom: 0;
}

.dropdown-vertical {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

img {
    max-height: 50px;
    max-width: auto;
}


.row .box-md,
.row .box-bg,
.row .box-md-ml-0 {
    transition: background-color ease-in-out 0.2s;
}

.row .box-md:hover,
.row .box-bg:hover,
.row .box-md-ml-0:hover {
    background-color: #ebebeb;
}

/*-------/----------------------------------------------*/
    
</style>
