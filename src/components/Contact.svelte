<script>
  let name = '';
  let email = '';
  let message = '';

  function handleSubmit() {
    alert(`Thank you, ${name}! Your message has been sent.`);
    name = '';
    email = '';
    message = '';
  }
</script>

<main>
  <h1>Contact Us</h1>
  <form on:submit|preventDefault={handleSubmit}>
    <div>
      <label for="name">Name:</label>
      <input type="text" id="name" bind:value={name} required>
    </div>
    <div>
      <label for="email">Email:</label>
      <input type="email" id="email" bind:value={email} required>
    </div>
    <div>
      <label for="message">Message:</label>
      <textarea id="message" bind:value={message} required></textarea>
    </div>
    <button type="submit">Send Message</button>
  </form>
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

  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 300px;
    margin: 0 auto;
  }

  div {
    width: 100%;
    margin-bottom: 1em;
  }

  label {
    display: block;
    margin-bottom: 0.5em;
    font-weight: bold;
  }

  input, textarea {
    width: 100%;
    padding: 0.5em;
  }

  textarea {
    height: 100px;
  }

  button {
    background-color: #40b3ff;
    color: white;
    border: none;
    padding: 0.5em 1em;
    font-size: 1em;
    cursor: pointer;
  }

  button:hover {
    background-color: #2090ff;
  }
</style>