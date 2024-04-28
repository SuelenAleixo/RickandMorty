<script setup>
import { onMounted, reactive, ref } from 'vue';
import ListPersonagens from '../components/ListPersonagens.vue';

let personagens = reactive(ref());

onMounted(() => {
  fetch("https://rickandmortyapi.com/api/character/?page=1")
  .then(response => response.json())
  .then(response => {
    personagens.value = response.results
    console.log(personagens)
  })
})

</script>

<template>
  <p class="text-center"
    style="font-size: 50px; font-weight: bold; background: linear-gradient(to right, #2ffd36, #000000);
            color: transparent; background-clip: text;">
    LISTAGEM DOS PERSONAGENS
  </p>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div class="col-md-12 col-md-6">
          <div class="card">
            <div class="card-body row">
              <ListPersonagens
                v-for="personagem in personagens" 
                :key="personagem.name" 
                :name="personagem.name"
                :url="personagem.url"
                :status="personagem.status"
                :species="personagem.species"
                :gender="personagem.gender"
                :location="personagem.location.name"
                :episode="personagem.episode"
                />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style>
</style>
