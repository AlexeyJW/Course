<template>
   <nav style="display: flex; gap: 10px;">
      <nuxt-link to="/">Home</nuxt-link> 
      <nuxt-link to="/movies">Movies</nuxt-link>
      <nuxt-link to="https://jw.org">JW.ORG</nuxt-link>
    </nav>  
    <slot></slot>
</template>