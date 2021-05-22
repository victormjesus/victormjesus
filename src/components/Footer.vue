<!--
|---------------------------------------------
| Footer Component 
|---------------------------------------------
| @usage Import the component and use, no params
| Main Footer Component
-->


<template>
    <div class='container-fluid text-center mt-5'> 
        <div class='row' id="footer">
            <div class="col-md-6 text-center">
                <div class='row'>
                    <div class="col">
                        <h1>Nossas Redes</h1>
                    </div>
                </div>
                <div class="row logos-footer">
                    <div class='col-4'><img class='grow img-fluid' src="../../assets/img/App/Footer/face.png"></div>
                    <div class='col-4'><img class='grow img-fluid' src="../../assets/img/App/Footer/linkedin.png"></div>
                    <div class='col-4'><img class='grow img-fluid' src="../../assets/img/App/Footer/youtube.png"></div>
                </div>
            </div>

            <div class="col-md-6">
                <div class='row'>
                    <div class="col">
                        <h1 id='desenvolvimento'>Desenvolvimento</h1>
                    </div>
                </div>
                <div class='row'>
                    <div class="col-6"><img id='lepes-logo' width='60' height='60' class='grow img-fluid' src="../../assets/img/App/Footer/lepes.png"></div>
                    <div class='col-6'><img width='80' height='80' class='grow img-fluid move-icon' src="../../assets/img/App/Footer/move.png"></div>
                </div>
            </div>
        </div>
        <div class="row bg-rodape">
            <div class="col text-center">
                <h3>© Plataforma Nacional - 2021</h3>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style scoped>
#footer {
    background-color: #fffdfd;
    width: auto;
    padding: 3rem 2rem 2rem;
    display: grid;
    grid-template-columns: repeat(2, minmax(250px, 1fr));
    gap: 2rem 0;
    box-shadow: 0px -10px 38px -12px rgb(96 133 236 / 35%)
}

#footer h1 {
    font-size: 1.8rem;
    font-weight: 100;
}

#footer div{
    justify-self: center;
}

.bg-rodape{
    background-color: #fffdfd;
}

/* .footer-left {
    width: 50%;
    height: 16rem;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 2rem;
}

.footer-right {
    width: 50%;
    height: 16rem;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 0.60rem;
} */

.logos-footer img {
    margin: 0.8rem;
    max-height: 4rem;
    transition: all .3s ease-in-out; 
 }

 .move-icon {
    height: 3.5rem;
    width: 5rem;
 }

 .logos-footer img:hover {
    transform: scale(1.06); 
 }

 .img-fluid {
     cursor: pointer;
 }

 @media only screen and (max-width:576px) {
     .footer-left{
         margin-top: 5rem;
     }

    .footer-right{
         margin-top: 0.65rem;
     }

     h3{
	    margin-top: 2rem;
     }

     #lepes-logo{
         margin: 0.5rem 0rem;
     }

     #footer{
         grid-template-columns: 1fr;
     }
    
     #footer h1 {
	    font-weight: 100;
     }

}

 h3 {
     text-align: center;
     font-size: 0.9rem;
     color: #878787;
 }

</style>
