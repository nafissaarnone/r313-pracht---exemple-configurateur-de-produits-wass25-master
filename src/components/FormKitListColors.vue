<script setup lang="ts">
import { colors } from "@/types";
defineProps<{
    name: string,
    label: string,
}>();

</script>
<template>
    <FormKit :name="name" :label="label" value="#FFFFFF" type="radio" :options="colors">

        <template #label="context">
            <div class="h-6 w-6 rounded-full" :style="{backgroundColor: context.option.value}"></div>
            <span>{{ context.option.label}}</span>
        </template>
    </FormKit>
</template>