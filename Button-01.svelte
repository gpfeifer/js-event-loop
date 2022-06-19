<script>
	let count = 0;

	function handleClick() {
	  count += 1;
	}
</script>

<style>
			button {
			  background: #134616;
			  color: rgb(255, 255, 255);
			  border: none;
			  padding: 8px 12px;
			  border-radius: 2px;

			  font-family: Arial, Helvetica, sans-serif;
			  font-size: 22px;
			}
</style>

<button on:click={handleClick}>
  Clicked {count} {count === 1 ? 'time' : 'times'}
</button>