<script>
  import Button from "./Button.svelte";
  import ButtonBlocking from "./ButtonBlocking.svelte";
</script>

<style>
  main {
    font-family: sans-serif;
    text-align: center;
  }
</style>

<main>
	<h1>Hello Event Loop</h1>
	<h2>It is single threaded!</h2>
	<Button />
  <p/>
  <ButtonBlocking />
  

</main>