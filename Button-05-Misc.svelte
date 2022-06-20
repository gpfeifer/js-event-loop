<script>
  function misc(iterator) {
    //let n = iterator.next();
    console.log(iterator);
    console.log([asy(1), asy(2)]);
  }

  async function asy(i) {
    let promise = new Promise(function(resolve, reject) {
      resolve(i * 2);
    });
    promise;
  }

  function handleClick() {
    misc([1, 2, 3].map(n => asy(n)));
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

<p/>
<button on:click={handleClick}>
  Misc
</button>