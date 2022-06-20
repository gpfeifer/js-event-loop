<script>
		let text = "Not called";

		function click1() {
		  text = fetch1("3");
		  console.log("end of click", text);
		}

		async function click() {
		  text = await fetch5("3");
		  console.log("end of click", text);
		}

		function fetch1(seconds) {
		  fetch("https://warp-wait.fly.dev/wait/" + seconds)
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

		//function fetchPromise

		async function fetch3(seconds) {
		  let startTime = performance.now();
		  await fetch2("1");
		  await fetch2("1");
		  let result = await fetch2("1");
		  let time = performance.now() - startTime;
		  console.log("end of fetch3", time);
		  return result + " " + time + " ms";
		}

		async function fetch4(seconds) {
		  let startTime = performance.now();

		  let result = await Promise.all([1, 1, 1, 1, 1].map(sec => fetch2(sec)));
		  console.log(result);
		  let endTime = performance.now();
		  console.log("end of fetch4", endTime - startTime);
		  return "time " + (endTime - startTime);
		}

		async function fetch5(seconds) {
		  let startTime = performance.now();
		  const urls = [
		    "https://warp-wait.fly.dev/wait/1",
		    "https://warp-wait.fly.dev/wait/1",
		    "https://warp-wait.fly.dev/wait/1"
		  ];

		  const responses = await Promise.all(urls.map(url => fetch(url)));
		  const errors = responses.filter(response => !response.ok);
		  if (errors.length > 0) {
		    throw errors.map(response => Error(response.statusText));
		  }
		  const [r1, r2, r3] = await Promise.all(
		    responses.map(response => response.text())
		  );
		  let time = performance.now() - startTime;
		  console.log(r1, r2, r3);
		  console.log("end of fetch4", time);
		  return "f5 " + r1 + " time " + time;
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
