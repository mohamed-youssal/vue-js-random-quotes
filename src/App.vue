<template>
  <div class="container" style="height: 100%; width: 100%;">
    <div class="row m-2">
      <div class="col-8 mx-auto text-center mt-5">
        <h2 class="text-light">RANDOM QUOTES:</h2>
      </div>
      <div class="col-8 mx-auto">
        <div class="card bg-light border-info mt-5">
          <div class="card-body text-center">
            <blockquote class="blockquote">
              <p class="font-italic h4">"{{ quote.quote }}"</p>
              <footer class="card-blockquote h6">{{ quote.character }} | <cite title="Source title">{{ quote.anime }}</cite></footer>
            </blockquote>
          </div>
        </div>
      </div>
      <div class="col-8 text-center mx-auto mt-5">
        <button @click="getData" class="btn btn-primary">Next random quote</button>
      </div>
    
    </div>
  </div>
    
</template>

<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios'

const quote = ref({})


onMounted(() => {
      getData(); // Call the fetchData function when the component is mounted
    });

const getData = async () => {
	await axios.get('https://animechan.xyz/api/random')
          .then(res => quote.value = res.data)
          .catch(error => console.log(error));
          }



</script>

<style>

</style>