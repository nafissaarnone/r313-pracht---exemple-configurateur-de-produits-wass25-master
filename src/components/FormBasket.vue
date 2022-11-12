<script setup lang="ts">

import type { Basket } from "@/types";
import { ref } from "vue";

import BasketProfil from "./BasketProfil.vue";
import BasketDessus from "./BasketDessus.vue";
import FormKitListColors from "./FormKitListColors.vue";

const props = defineProps(["id"]);
const Baskete = ref<Basket>({});

async function upsertBasket(dataForm, node) {
    const { data, error } = await supabase.from("Chaussure").upsert(dataForm);
    if (error) node.setErrors([error.message]);
    else {
        node.setErrors([]);
        router.push({ name: "basket-edit-id", params: { id: data[0].id } });
    }
}

if (props.id) {
    let { data, error } = await supabase
        .from("Chaussure")
        .select("*")
        .eq("id_chaussure", props.id);

    if (error) console.log("n'a pas pu charger le table Chaussures :", error);
    else Baskete.value = (data as any[])[0];
}

</script>



<template>
    <div class="p-2">
        <ul class="flex gap-1">
            <li><a href="#profil">Profil</a></li>
            <li><a href="#dessus">Dessus</a></li>
        </ul>

        <div class="carousel w-64">
            <BasketProfil class="carousel-item w-64" v-bind="Baskete" id="profil" />
            <BasketDessus class="carousel-item w-64" v-bind="Baskete" id="dessus" />
        </div>

        <FormKit type="form" v-model="Baskete" @submit="upsertBasket">
            <FormKitListColors name="semelle" label="semelle" />
            <FormKitListColors name="empeigne" label="empeigne" />
            <FormKitListColors name="pointe" label="pointe" />
            <FormKitListColors name="oeillet" label="oeillet" />
            <FormKitListColors name="bande" label="bande" />
            <FormKitListColors name="languette" label="languette" />
            <FormKitListColors name="lacet" label="lacet" />
            <FormKitListColors name="trimestre" label="trimestre" />

        </FormKit>
    </div>
</template>
