<!--
|---------------------------------------------
| ListTeams Component 
|---------------------------------------------
| @usage Import the component and use, no params
| List all teams and show its filters
-->
<template> 
    
    <Navbar/>
    <div class="list-teams">

        <!-- <Panel 
            :infos="infosPanel"
            :teams="teams"
        /> -->

        <div class="container mt-5" v-if="Object.keys(teams).length != 0">
            <!-- INICIO DO FORM DE FILTRAGEM -->
            <form @submit.prevent="" class="form-inline">
                <div class="form-group">
                
                <!-- DROPDOWN DE SELECAO DE FILTRO -->
                <label class="mr-sm-2 text-nowrap label-filtro" for="inlineFormCustomSelect">Filtrar por: </label>
                    <Filter ref="filtersearchname" @click="setSelectedValue()" :optionsSelect="options" nameSelect="filtro_instituicoes" id="inlineFormCustomSelect"/>
                </div>

                <!-- SE A SELECAO FOR NOME (2) ENTAO EXIBIRA OS SUBFILTROS DE NOME -->
                <div class="form-group" v-if="selectedValue == 2">
                    <label class="mr-sm-2 text-nowrap label-filtro" for="inlineFormCustomName">Digite o nome: </label>
                    <input class="input-personal mr-sm-4" v-model="searchByName" type="text" name="filtro_nome_instituicoes" id="inlineFormCustomName" autocomplete="off">
                
                    <input class="radio-personal mr-sm-2" v-model="searchWithOrder" value="cres" type="radio" name="filtro_nome_ordenacao" id="inlineFormCustomRadioAZ" checked>
                    <label class="mr-sm-2 text-nowrap label-filtro mr-sm-4" for="inlineFormCustomRadioAZ">A - Z</label>
                    
                    <input class="radio-personal mr-sm-2" v-model="searchWithOrder" value="desc" type="radio" name="filtro_nome_ordenacao" id="inlineFormCustomRadioZA">
                    <label class="mr-sm-2 text-nowrap label-filtro" for="inlineFormCustomRadioZA">Z - A</label>
                </div>

                <!-- SE A SELECAO FOR POR GRUPOS (3) ENTAO EXIBIRA OS SUBFILTROS DOS GRUPOS -->
                <div class="form-group" v-if="selectedValue == 3">
                    <label class="mr-sm-2 text-nowrap label-filtro" for="inlineFormCustomCodigo">Selecione o grupo: </label>
                    <Filter ref="filtersearchgroup" @click="setSelectedGroup()" :optionsSelect="group_options" nameSelect="filtro_grupo_instituicoes" id="inlineFormCustomCodigo"/>
                </div>

            </form>
        </div>

        <transition-group tag="div" v-if='filterInstituicao' class="cards mt-5" name="listanimate">
    
            <div class="card-personal mb-4"  v-for="team in filterInstituicao" :key="team.id">
            
            <CardsBG 
                :id="team.id" 
                :name="team.name"
                :nr_members="team.nr_members" 
                :nr_sample="team.nr_sample" 
                :thumbnail="team.thumbnail"
            />
            </div>

        </transition-group>

        <transition-group v-else>
            <noMatchesFound 
                message="Nenhum resultado encontrado. Por favor, tente novamente."
                />
        </transition-group>
    
    <Footer/>
    
    </div>
    
</template>

<script>

import CardsBG from './components/CardsBG';
import Filter from './components/Filter';
import noMatchesFound from './components/noMatchesFound';
// import Panel from './components/Panel';
import Navbar from './components/Navbar'; 
// import Footer from './components/Footer';

// import axios from "axios";

export default {
    name: 'ListTeams',
    data() {
        return {
        qtdTeams: 0,
        selectedValue: '',
        searchByName: '',
        searchByCode: '',
        searchWithOrder: '',
        selectedGroupFilter: 0,
        teams: [
            {
            id:1,
            name: 'Secretaria da Educação do Estado de São Paulo',
            nr_members: 2,
            nr_sample: 3,
            gp_research: 'LEPES X',
            thumbnail: 'instituicao2.jpg'
            },

            {
            id:2,
            name: 'Secretaria da Educação do Estado de Minas Gerais',
            nr_members: 2,
            nr_sample: 50000,
            gp_research: 'Secretaria X',
            thumbnail: 'instituicao3.jpeg'
            },

            {
            id:3,
            name: 'Secretaria da Educação do Estado de Ceará',
            nr_members: 5,
            nr_sample: 2,
            gp_research: 'LEPES X',
            thumbnail: 'instituicao4.jpg'
            },

            {
            id:4,
            name: 'Secretaria da Educação de Manaus',
            nr_members: 4,
            nr_sample: 50000,
            gp_research: 'Secretaria X',
            thumbnail: 'instituicao1.jpg'
            },
            {
            id:5,
            name: 'Universidade de São Paulo',
            nr_members: 20,
            nr_sample: 43,
            gp_research: 'Secretaria X',
            thumbnail: 'instituicao5.jpg'
            },
            {
            id:6,
            name: 'Universidade Federal de Paraíba',
            nr_members: 90,
            nr_sample: 53942,
            gp_research: 'LEPES X',
            thumbnail: 'instituicao6.jpg'
            }
        ],
        

        options: [
            {
            id:1,
            value: 'Todos'
            },
            {
            id:2,
            value: 'Nome'
            },
            {
            id:3,
            value: 'Grupo de Pesquisa'
            }
        ],
        group_options: [
            {
            id:1,
            value: 'Todos'
            },
            {
            id:2,
            value: 'LEPES X'
            },
            {
            id:3,
            value: 'Secretaria X'
            }
        ],

        infosPanel: {
            title: 'Instituições',
            firstButtonTitle: 'Buscar Instituição',
            firstButtonText: 'Faz parte de alguma instituição? Encontre-o e solicite sua entrada',
            secondButtonTitle: 'Criar Instituição',
            secondButtonText: 'Faz parte de alguma instituição? Encontre-o e solicite sua entrada'
        }
        }
    },
    components: {
        CardsBG,
        Filter,
        noMatchesFound,
        // Panel,
        Navbar,
        // Footer
    },
    methods: {
        setSelectedValue () {
            this.selectedValue = this.$refs.filtersearchname.value
        },
        setSelectedGroup () {
            this.selectedGroupFilter = this.$refs.filtersearchgroup.value
        }
    },

    // Utilizando a API


    // created(){
    //     axios
    //     .get("http://localhost:3000/insti/count", {
    //         headers: { 
    //             'Authorization': 'Bearer ' + localStorage.getItem('accessToken')
    //         }  
    //     })

    //     .then((response) => this.teams = response.data)
    //     .catch((error) => console.log(error))
    //     .finally(() => (this.loading = false));
    // },
    mounted: function() {
         this.qtdTeams = Object.keys(this.teams).length;
    },
    computed: {

        filterInstituicao: function() {
            
            //VARIAVEL QUERY INICIA COM TODOS OS ITENS DO ARRAY
            var query = this.teams;
            query = query.sort((a, b) => a.name.localeCompare(b.name));

            //CASO SEJA SELECIONADO TODOS, EXIBE TODOS OS ITENS DO ARRAY
            if (this.selectedValue == 1) {
                query = this.teams;
                query = query.sort((a, b) => a.name.localeCompare(b.name));
            }

            //CASO SEJA SELECIONADO NOME, FILTRA POR NOME
            else if (this.selectedValue == 2) {

                //SE ESTIVER VAZIO O CAMPO DE BUSCA RETORNA TODOS
                if (this.searchByName.trim() == '') {
                    query = this.teams;
                }
                //SENAO ELE FILTRA PELO O QUE FOR DIGITADO
                else {

                    var filtered = this.teams.filter(team =>team.name.trim().toLowerCase().match(this.searchByName.trim().toLowerCase()))

                    if(filtered.length != 0){
                       query = filtered
                    }

                    else{
                       query = false
                    }

                }

                //ORDERNA CRESCENTEMENTE
                if (this.searchWithOrder == 'cres') {
                    query.sort((a, b) => a.name.localeCompare(b.name));
                }

                //ORDERNA CRESCENTEMENTE
                if (this.searchWithOrder == 'desc') {
                    query.reverse((a, b) => a.name.localeCompare(b.name));
                }

            }

            //CASO SEJA SELECIONADO GRUPO DE PESQUISA, FILTRA POR GRUPO
            else if (this.selectedValue == 3) {
            
                if (this.selectedGroupFilter == 0){
                    query = this.teams;
                }

                else if (this.selectedGroupFilter == 1){
                    query = this.teams;
                }

                else if (this.selectedGroupFilter == 2) {
                    query = this.teams.filter(team => team.gp_research == 'LEPES X')
                }
                
                else if (this.selectedGroupFilter == 3) {
                    query = this.teams.filter(team => team.gp_research == 'Secretaria X')
                }
            }
            
            return query;
        }
    }
}
    
</script>

<style>

  @import 'assets/css/uicons-regular-rounded.css';
  @import 'assets/css/uicons-solid-rounded.css';

  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Hind', sans-serif;
    scroll-behavior: smooth;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background-image: linear-gradient(to bottom, #edf0f7, #e8ecf5, #e3e8f4, #dee5f2, #d9e1f0);
    /* Gradiente 1 */
    background: linear-gradient(180deg, #EDF0F7 0%, #D9E1F0 100%), #C4C4C4;
    /* Gradiente 2 */
    background: linear-gradient(180deg, #EEF5FD 0%, #E1E7F1 100%);
    /* Gradiente 3 */
    background: linear-gradient(180deg, #F1F6F9 0%, #F1F6F9 50.52%, #D2E3EA 100%);

    /* Original */
    /* background: linear-gradient(180deg, #D5E8FE 0%, rgba(255, 255, 255, 0) 80%), #FEFEFE; */
  }

  h2{
    color: #105B9F;
    font-weight: bold;
  }

  .ml-6 {
    margin-left: 6rem;
  }

  .boas-praticas h1{
    color: #41B3A3;
  }

  .materiais-documentos h1{
    color: #EB7071;
  }

  .certificacao h1{
    color: #F498C0;
  }

  .dados h1{
    color: #0d9f9f;
  }

  .grow { 
    transition: all .2s ease-in-out; 
  }

  .grow:hover { 
    transform: scale(1.035); 
  }

  .itens-modal {
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
  }

  .titulo-modal {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin: 2rem;
      font-size: 1.3rem;
      text-transform: uppercase;
      font-weight: bold;
      color:rgb(67, 70, 78);
  }

  .exit {
      cursor: pointer;
  }

  .select-personal,
  .input-personal {
    border-radius: 8px;
    background: #FCFCFC;
    outline: none;
    border: 1px solid rgba(0, 0, 0, 0.11);
    font-weight: lighter;
    padding: 0.2rem 0.4rem;
    box-shadow: 1px 2px 6px -3px rgba(0, 0, 0, 0.25);
  }

  .input-personal {
    padding: 0.2rem 0.4rem;
    font-size: 20px;
  }

  .radio-personal {
    height: 18px;
    width: 18px;
  }

  .btn-router-link,
  .btn-router-link:hover,
  .btn-router-link:focus {
    text-decoration: none;
  }

  .cool-link {
      display: inline-block;
  }

  .cool-link::after {
      content: '';
      display: block;
      width: 0;
      height: 0.1rem;
      background-color: #252525;
      transition: width .4s;
      margin-top: 0.1rem;
  }

  .cool-link:hover::after {
      width: 100%;
      transition: width .4s;
  }

    .list-teams {
        min-height: 90vh;
        padding-top: 2rem;
    }

    .about-team {
        background-color: rgb(255, 255, 255);
        display: flex;
        align-items: center;
        justify-content: space-around;
        border-radius: 12px;
        padding: 1rem 4rem;
    }

    .img-about-team {
        max-height: 16rem;
    }

    .box-btn-about-team button {
        background-color: transparent;
        outline: none;
        cursor: pointer;
        padding: .3rem .8rem;
        border-radius: 6px;
        color: #105B9F;
        border: 3px solid #105B9F;
        font-size: 1.1rem;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    .box-btn-about-team i {
        font-size: 1.3rem;
    }

    .label-filtro {
        font-weight: 600;
    }

    /* Código para centralizar os cards como se fosse 
       (flex-start + div centralizada) */
    .cards {
       display: grid;
       grid-template-columns: repeat(3, minmax(21rem, max-content));
       grid-gap: 1.8rem;
       justify-content: center;
    }

    /* Responsoivizando alinhamento dos cards */
    @media screen and (max-width: 1160px) {
    .cards { 
       grid-template-columns: repeat(auto-fit, minmax(21rem, max-content));
    }
    }

    .card-personal {
        width: 21rem;
    }

    .card.custom-rounded {
        border-radius: 20px;
        box-shadow: 12px 12px 23px -7px rgba(158,146,158,0.49);
    }

    .filter-box {
        margin: 2rem 4rem 2rem 0;
        margin-left: 6.5vw;
    }

    .card-body {
        text-align: center;
        font-weight: bold;
        min-height: 116px;
    }

    .card-text {
        padding-top: 1rem;
        color: #212529;
        font-size: 1rem;
    }

    .card-img-top {
        cursor: pointer;
    }

    @media screen and (max-width: 1012px) {
        .filter-box {
            display: flex;
            align-items: center;
            justify-content: center;
        }
    }

    .listanimate-enter-active,
    .listanimate-leave-active {
        transition: all 0.4s;
    }

    .listanimate-enter, 
    .listanimate-leave-to  {
        transform: scale(0);
        opacity: 0;
    }

</style>