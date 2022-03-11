<script lang="ts">
  import logo from './assets/svelte.png'
  import './app.css'
  import {onMount} from 'svelte';
  import MainText from './lib/MainText.svelte'
  
</script>
<main>
  <MainText/> 
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }


</style>
