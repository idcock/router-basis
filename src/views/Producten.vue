<template>
    <div class="producten">
        <h1>Producten</h1>
        <h2>Bekijk onze fantastische producten</h2>
        <div class="producten-lijst">
            <div class="product-kaart" v-for="product of producten" :key="product.id">
                 <header class="product-header">    
                    {{product.naam}}       
                </header>
                <figure class="image-container">
                    <img :src="maakAfbeeldingUrl(product)"
                        :alt = "`afbeelding van ${product.naam}`" >
                    <figcaption class = "product-prijs">
                        &euro;{{product.prijs}}
                    </figcaption>
                </figure>
               
            </div>
        </div>
    </div>
    
</template>

<script>
// @ is een alias voor de rootmap (src)
import {producten,categories} from '@/producten.js'

export default {
    data() {
        return {
            //we stoppen in variabele producten de geimporteerde array producten
            // met enkel te importeren kunnen we niet aan de producten
            producten:producten,
            categories:categories,
            // process.env geeft ons toegang tot omgevingsvariabelen van het project
            // de eigenschap BASE_URL wordt door Vue ingevuld met het absolute adres van de webapplicatie
            baseUrl:process.env.BASE_URL,

        }
    },
    methods: {
        maakAfbeeldingUrl(product){
            // geen slash achter this.baseUrl, want deze variabele bevat op het einde al een slash
            return `${this.baseUrl}producten/${product.categorie}/${product.afbeelding}`;
               }
    },
   
}
</script>

<style scoped>
.producten {
    display:flex;
    flex-direction: column;
    align-items:center;
    padding-top: 5rem;
}

h1 {
    font-size: 7rem;
    color:#40B782;
}

.producten-lijst{
   width:80%;
   display:grid;
   grid-template-columns: repeat(auto-fit,minmax(300px,1fr)) ;
   column-gap: 5rem;
   row-gap: 5rem;
}

.product-kaart{
text-align: center;
}

.image-container img{
height: 250px;
}



</style>
