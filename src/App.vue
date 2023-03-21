<script setup>
import {RouterView} from 'vue-router'
</script>

<template>
<div class="top">
      <header class="content-header">
  <div class="row">
    <div class="button col">
      <a href="/" class="btn btn-primary" role="button" aria-pressed="true">Home</a>
    </div>
    <div class="dropdown col">
      <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown" id="dropdownMenuButton1"
        aria-expanded="false">
        OpenApi
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
        <li><a class="dropdown-item" href="http://10.44.192.51:44010/nVentoryOpenAPI.html">nVentory</a></li>
        <li><a class="dropdown-item" href="#">nView</a></li>
        <li><a class="dropdown-item" href="#">Owl</a></li>
      </ul>
    </div>
    <div class="dropdown col">
      <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown" id="dropdownMenuButton2"
        aria-expanded="false">
        Notes
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton2">
        <li><a class="dropdown-item" href="/nVentoryNotes">nVentory</a></li>
        <li><a class="dropdown-item" href="/nViewNotes">nView</a></li>
        <li><a class="dropdown-item" href="/nPortNotes">nPort</a></li>
        <li><a class="dropdown-item" href="/xPortNotes">xPort</a></li>
        <li><a class="dropdown-item" href="/MiscNotes">misc</a></li>
      </ul>
    </div>
    <div class="dropdown col">
      <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown" id="dropdownMenuButton3"
        aria-expanded="false">
        QA
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton3">
        <li><a class="dropdown-item" href="#">Support</a></li>
        <li><a class="dropdown-item" href="#">Internal</a></li>
      </ul>
    </div>
  </div>
  <RouterView />
  </header>
  </div>
</template>