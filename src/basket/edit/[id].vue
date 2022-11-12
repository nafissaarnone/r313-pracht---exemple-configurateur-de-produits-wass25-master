<script setup lang="ts">

import FormBasket from "../../components/FormBasket.vue";

defineProps({ id: String });

</script>




<template>

    <div class="border-0">

        <FormBasket :id="id" />

    </div>

</template>