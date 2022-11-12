<script setup lang="ts">
import { supabase } from "@/supabase";
import BasketProfil from "./BasketProfil.vue";

const props = defineProps<{
    max?: number;
}>();

let { data: Basket, error } = await supabase
    .from("Chaussure")
    .select("*")
    .limit(props.max ?? 100)

if (error) {
    console.log("erreur données Basket", { error });
}
</script>

<template>
    <ul>
        <li v-for="basket in Basket" :key="basket.id_chaussure">
            <router-link :to="{ name: 'basket-edit-id', params: { id: basket.id_chaussure } }">
                <BasketProfil class="w-64" v-bind="basket" />
            </router-link>
        </li>
    </ul>
</template>