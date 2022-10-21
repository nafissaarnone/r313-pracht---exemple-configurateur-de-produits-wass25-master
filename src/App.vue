<template>
  <nav>
    <ul>
      <li>
        <router-link class="text-red-600 underline" to="/">
          Liste d'exemple
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/basket/new">
          Personnaliser une Basket
        </router-link>
      </li>
    </ul>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>

    <router-view class="m-2 border-2 p-2" />

  </Suspense>

  <LoginLogout></LoginLogout>

</template>

<script setup lang="ts">
import { Bars3Icon } from '@heroicons/vue/20/solid'
import LoginLogout from './components/LoginLogout.vue'
</script>
