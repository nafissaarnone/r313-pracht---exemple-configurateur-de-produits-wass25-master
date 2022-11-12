<script setup lang="ts">

import exemples from "../public/exemples.json";
import BasketProfil from "../src/components/BasketProfil.vue";
import BasketDessus from "../src/components/BasketDessus.vue"



</script>




<template>

    <div class="flex gap-5 border-0">

        <div v-for="exemple in exemples" :key="exemple.semelle">

            <BasketProfil class="carousel-item w-64" v-bind="exemple" id="profil" />
            <BasketDessus class="carousel-item w-64" v-bind="exemple" id="dessus" />

        </div>

    </div>

</template>