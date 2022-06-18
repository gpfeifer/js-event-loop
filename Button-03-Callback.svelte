<script>
	let text = "Not called";

	function get() {
	  const xhttp = new XMLHttpRequest();
	  xhttp.onreadystatechange = function() {
	    console.log("callback ", xhttp.status);
	    if (xhttp.readyState == 4 && xhttp.status == 200) {
	      text = "done";
	    } else {
	      text = "error";
	    }
	  };
	  xhttp.open("GET", "warp-wait.fly.dev/wait/3", true);
	  xhttp.send();
	  console.log("send");
	}
</script>

<style>
	button {
	  background: #134616;
	  color: rgb(255, 255, 255);
	  border: none;
	  padding: 8px 12px;
	  border-radius: 2px;
	}
</style>

<p>
<button on:click={get}>
  Callback
</button>
</p>
<p id="text">{text}</p>
