<script>
	let text = "Not called";

	function get() {
	  const xhttp = new XMLHttpRequest();
	  xhttp.onload = function() {
	    console.log("callback ", xhttp.status, xhttp.readyState);
	    if (xhttp.status == 200) {
	      text = "done";
	    } else {
	      text = "error";
	    }
	    let n = 0;
	    while (n > 0) {
	      n--;
	    }
	  };
	  xhttp.open("GET", "https://warp-wait.fly.dev/wait/10", true);
	  xhttp.send();
	  console.log("send");
	}

	function click() {
	  get();
	  console.log("end of click");
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
<button on:click={get}>
  Callback {text}
</button>
</p>
<p id="text">{text}</p>
