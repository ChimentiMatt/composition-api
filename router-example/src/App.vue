<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="wrapper">
    <HelloWorld msg="You did it!" />

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <br><br/>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </div>

  <RouterView />
</template>

=
