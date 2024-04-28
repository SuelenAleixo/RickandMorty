<script setup>
const personagem = defineProps(["name", "url", "status", "species", "gender", "location", "episode"])
const personagemId = personagem.url.split('/')[5]
const imageUrl = "https://rickandmortyapi.com/api/character/avatar/" + personagemId + ".jpeg"
const episode = "https://rickandmortyapi.com/api/episode"
console.log(imageUrl)
</script>

<template>
    <div class="col-md-4">
        <div class="card p-2 mb-3" style="height:600px">
            <img :src="imageUrl" style="border-radius: 5px; height: 350px">
            <div class="desccricao" style="font-weight: bold; font-size: 17px">
                <p class="text-center">Nome: {{personagem.name}}</p>
                <p class="text-center">Status: {{personagem.status}}</p>
                <p class="text-center">Espécie: {{personagem.species}}</p>
                <p class="text-center">Gênero{{personagem.gender}}</p>
                <p class="text-center">Localização: {{personagem.location}}</p>
                <p class="text-center">Qta. de aparições: {{personagem.episode.length}}</p>
            </div>
        </div>
    </div>
</template>

<style>

</style>