<script setup lang="ts">

import exemples from "../../public/exemples.json";
import BasketProfil from "../../src/components/BasketProfil.vue";
import BasketDessus from "../../src/components/BasketDessus.vue"
import ListeBasket from "../components/ListeBasket.vue"
import { user } from "@/supabase";



</script>




<template>

  <div>
    Exemple de Basket
    <div class="flex" v-for="exemple in exemples" :key="exemple.semelle">
      <BasketProfil class="carousel-item w-64" v-bind="exemple" id="profil" />
      <BasketDessus class="carousel-item w-64" v-bind="exemple" id="dessus" />

    </div>

    <section v-if="user">
      <h2>
        un extrait de vos chaussures (<RouterLink class="text-red-600 underline" to="/basket">Toutes les voir
        </RouterLink>)
      </h2>
      <ListeBasket class="flex flex-wrap gap-2" :max="2" />
    </section>

  </div>

</template>