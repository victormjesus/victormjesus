<!--
|---------------------------------------------
| CardsBG Component 
|---------------------------------------------
| @usage Import the component and use
| <CardsBG :name="team.name" 
|   :nr_members="team.nr_members" 
|   :nr_application="team.nr_application" 
|   thumbnail="img-escola.png"/>
-->

<template>

    <div class="">

        <div @click="closeMiniDropdown()" class="overlay-invisible" :class="{'overlay-visible': isActiveMiniDropdown}"></div>

        <!-- CARDS DAS INSTITUIÇÕES -->
        <div class="card custom-rounded">
            <router-link :to="{name: 'InstituicaoMenu', params: { idInstituicao: idInstituicao }}">

                <!-- TODO (Resolvido) José - Cog fora de eixo -->

                <div @mouseenter="turnOnCog()" @mouseleave="turnOffCog()" class="box-img-card">
                    <img class="card-img-top" :src="require('../assets/img/Dados/ListarInstituicao/Instituicoes/'+ thumbnail)" alt="Card image cap "/>
                </div>
            </router-link>
            <div @click="showMiniDropdown()" class="institution-actions">
                <!-- <span>Ações da Instituição </span> -->
                <i class="fas fa-cog text-secondary" :class="{'turning-cog': isTurningCog, 'turning-instead-cog': isTurningInsteadCog}" ></i>
                <div class="dropdown-box" :class="{'dropdown-box-visible': isActiveMiniDropdown}">
                    <div class="mini-dropdown">
                        <!-- TRIÂNGULO DO POP-UP PEQUENO -->
                        <div class="mini-triangle"> 
                            <svg class="triangulo-1" width="26" height="30" viewBox="0 0 36 33" xmlns="http://www.w3.org/2000/svg">
                                <path d="M13.6699 2.5C15.5944 -0.833332 20.4056 -0.833334 22.3301 2.5L35.3205 25C37.245 28.3333 34.8394 32.5 30.9904 32.5H5.00962C1.16062 32.5 -1.24501 28.3333 0.679492 25L13.6699 2.5Z" fill="white"/>
                            </svg>
                        </div>
                        
                        <!-- POP-UP PEQUENO -->
                        <div class="mini-pop-up shadow-lg pt-3 pr-1 pb-3 pl-2">
                            <div class="row-md-12 font-weight-light pl-0 pr-0 item-minidropdown"><i class="fas fa-info-circle mr-1"></i> Informações</div>
                            <div class="row-md-12 font-weight-light pl-0 pr-0 item-minidropdown"><i class="fas fa-sign-out-alt mr-1"></i> Deixar Equipe</div>
                            <div class="row-md-12 font-weight-light pl-0 pr-0 item-minidropdown"><i class="fas fa-trash mr-1"></i> Excluir</div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="card-body pt-1 pl-4 pr-4 pb-1">
                <p class="card-text mb-0"><strong>{{name}}</strong></p>
                <p class="text-secondary mb-0"> <i class="fas fa-user-friends mb-0 mr-1"></i>{{nr_members}} pessoas pertencem a essa equipe</p>
                <p class="text-secondary mb-0"> <i class="fas fa-layer-group mb-0 mr-1"></i>{{nr_sample}} aplicações foram feitas por essa equipe</p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'CardsBG',
    data() {
        return {
            idInstituicao: this.id,
            nomeInstituicao: this.name,
            isActiveMiniDropdown: false,
            isTurningCog: false,
            isTurningInsteadCog: false
        }
    },
    props: {
        id: Number,
        name: String,
        nr_members: Number,
        nr_sample: Number,
        thumbnail: String
    },
    methods: {
        showMiniDropdown: function() {
            this.isActiveMiniDropdown = true
        },
        closeMiniDropdown: function() {
            this.isActiveMiniDropdown = false
        },
        turnOnCog: function() {
            this.isTurningCog = true
            this.isTurningInsteadCog = false
        },
        turnOffCog: function() {
            this.isTurningCog = false
            this.isTurningInsteadCog = true
        }
    },
    mounted: function(){
        console.log(this.$route.params.idInstituicao)
    }
}
</script>

<style scoped>

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

    .card {
        border: none !important;
    }
    .card.custom-rounded {
        border-radius: 20px;
        box-shadow: 12px 12px 23px -7px rgba(158, 146, 158, 0.671);
    }

    .box-img-card {
        display: inline-block;
        overflow: hidden;
        border-top-left-radius: calc(1rem - 1px);
        border-top-right-radius: calc(1rem - 1px);
        height: 10rem;
    }   

    .card-img-top {
        cursor: pointer;
        display: block;
        height: 10rem;
        transition: transform .4s;
    }

    .card-img-top:hover {
        transform: scale(1.1);
        transform-origin: 50% 50%;
    }

    .fa-cog {
        color: rgb(221, 221, 221);
        font-size: 1rem;
    }

    .turning-cog {
        animation: turningCogAnimation;
        animation-duration: 0.6s;
        animation-timing-function: ease-in-out;
    }

    .turning-instead-cog {
        animation: turningCogInsteadAnimation;
        animation-duration: 0.6s;
        animation-timing-function: ease-in-out;
    }

    @keyframes turningCogAnimation {
        to {
            transform: rotate(360deg)
        }
    }

    @keyframes turningCogInsteadAnimation {
        to {
            transform: rotate(-360deg)
        }
    }

    .card-body {
        font-size: 0.9rem;
        min-height: 8rem;  
        display: flex;
        justify-content: center;
        flex-direction: column;
    }

    .mini-triangle{
        margin: 0rem;
        display: center;
        align-items: center;
        justify-items: center;
        position: absolute;
        top: -16%;
        left: 67%;

    }
    .dropdown-box {
        position: absolute;
        top: 150%;
        right: -41%;
        z-index: 2;
        opacity: 0;
        pointer-events: none;
        cursor: default;
        transition: all 0.4s ease;
    }

    .dropdown-box-visible{
        opacity: 1;
        cursor: pointer;
        pointer-events: all;
    }

    .mini-dropdown {
        position: relative;
    }

    .institution-actions{
        display: flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: 1rem;
        right: 1rem;
        font-size: 0.9rem;
        font-weight: bold;
        cursor: pointer;
        background: #FFF;
        border-radius: 100%;
        width: 32px;
        height: 30px;
        box-shadow: 1px 2px 6px -3px rgb(0 0 0 / 25%);
    }

    .mini-pop-up{
        height: 5.5rem;
        width: 8rem;
        background-color:white;
        color:grey;
        border-radius: 1rem;
        transition: color ease-in-out 0.2s;
    }

    .item-minidropdown:hover {
        color: rgb(58, 58, 58);
    }

</style>