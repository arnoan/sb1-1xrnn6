<script>
  import Nav from './components/Nav.svelte';
  import Home from './components/Home.svelte';
  import About from './components/About.svelte';
  import Contact from './components/Contact.svelte';
  import Experimental from './components/Experimental.svelte';
  
  let currentPage = 'home';
</script>

<Nav bind:currentPage />

{#if currentPage === 'home'}
  <Home />
{:else if currentPage === 'about'}
  <About />
{:else if currentPage === 'contact'}
  <Contact />
{:else if currentPage === 'experimental'}
  <Experimental />
{/if}

<style>
  :global(body) {
    margin: 0;
    font-family: Arial, sans-serif;
  }
</style>