<script>
  export let currentPage;
  
  let links = [
    { href: 'home', text: 'Home' },
    { href: 'about', text: 'About' },
    { href: 'contact', text: 'Contact' },
    { href: 'experimental', text: 'Experimental' }
  ];
</script>

<nav>
  <ul>
    {#each links as link}
      <li>
        <a 
          href="#{link.href}" 
          class:active={currentPage === link.href}
          on:click={() => currentPage = link.href}
        >
          {link.text}
        </a>
      </li>
    {/each}
  </ul>
</nav>

<style>
  nav {
    background-color: #333;
    padding: 1em;
  }

  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
  }

  li {
    margin: 0 1em;
  }

  a {
    color: white;
    text-decoration: none;
    font-weight: bold;
  }

  a:hover, a.active {
    text-decoration: underline;
  }
</style>