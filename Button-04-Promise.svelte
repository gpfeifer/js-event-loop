<script>
	let text = "Not called";

	async function click() {
	  text = await fetch4("3");
	  console.log("end of click", text);
	}

	function fetch1(seconds) {
	  fetch("https://warp-wait.fly.dev/wait/seconds")
	    .then(response => response.text())
	    .then(data => {
	      console.log("promise");
	      text = data;
	    });
	  console.log("end of get");
	  return "Pending";
	}

	async function fetch2(seconds) {
	  text = "Pending";
	  let response = await fetch("https://warp-wait.fly.dev/wait/" + seconds);
	  let result = await response.text();
	  return result;
	}

	async function fetch3(seconds) {
	  let startTime = performance.now();
	  await fetch2("1");
	  await fetch2("1");
	  let result = await fetch2("1");
	  let endTime = performance.now();
	  console.log("end of fetch3", endTime - startTime);
	  return result;
	}

	async function fetch4(seconds) {
	  let startTime = performance.now();
	  let vec = [() => fetch2("1"), () => fetch2("1"), () => fetch2("1")];
	  let result = Promise.all(vec);
	  let endTime = performance.now();
	  console.log("end of fetch4", endTime - startTime);
	  return result[0] + result[1];
	}
</script>

<style>
	button {
	  background: #134616;
	  color: rgb(255, 255, 255);
	  border: none;
	  padding: 8px 12px;
	  border-radius: 2px;
	  font-size: 22px;
	}
</style>

<p>
<button on:click={click}>
  Promise {text}
</button>
</p>
<p id="text">{text}</p>
