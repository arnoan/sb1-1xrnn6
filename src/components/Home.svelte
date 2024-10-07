<script>
  let name = 'World';
  
  function handleInput(event) {
    name = event.target.value;
  }
</script>

<main>
  <h1>Welcome to Our Svelte App</h1>
  <p>This is the home page of our simple Svelte application.</p>
  <h2>Hello, {name}!</h2>
  <input type="text" value={name} on:input={handleInput} placeholder="Enter your name">
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
  }

  h1 {
    color: #ff3e00;
    font-size: 2.5em;
  }

  h2 {
    color: #40b3ff;
    font-size: 2em;
  }

  input {
    width: 100%;
    max-width: 300px;
    padding: 0.5em;
    margin-top: 1em;
  }
</style>