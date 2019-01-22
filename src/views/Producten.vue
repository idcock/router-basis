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
                </figure>
                <footer class = "product-prijs">
                    &euro;{{product.prijs}}
                </footer>
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
            categories

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

</style>
