<script>
  import Button from "./Button-01.svelte";
  import ButtonBlocking from "./Button-02-Blocking.svelte";
  import ButtonCallback from "./Button-03-Callback.svelte";
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
  <ButtonCallback />
  
  

</main>