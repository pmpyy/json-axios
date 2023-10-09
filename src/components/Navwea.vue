<script setup>
import { RouterLink } from 'vue-router'
</script>
<template>
<div class="container-fluid">
  <nav class="navbar navbar-expand-lg body" style="background-color:  #DDEDF5;">
    <div class="container-fluid">
      <hr class="name"><RouterLink to="/"><img src="https://cdn-icons-png.flaticon.com/128/648/648198.png" alt="" style="max-width: 80px;"></RouterLink>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="true" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse name-top" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item name">
          <a class="nav-link active" aria-controls="page"><RouterLink to="/" >weather</RouterLink></a> 
        </li>
      </ul>
      
    </div>
    </div>
  </nav>
</div>
  
  
    
  </template>
<style>

a{
  text-decoration: none;
  color: #88A7B9;
  transition: 0.4s;
  padding: 10px;
  text-align: center;
}
nav a.router-link-exact-active {
  color: #222A2E;
  text-decoration-line: underline;
  
}







/* @media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }


  nav {
    text-align: center;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}  */
</style>