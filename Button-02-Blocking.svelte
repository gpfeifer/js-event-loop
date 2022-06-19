<script>
  let result = "Ready";
  function calculatePrimes(iterations, multiplier) {
    var primes = [];
    for (var i = 0; i < iterations; i++) {
      var candidate = i * (multiplier * Math.random());
      var isPrime = true;
      for (var c = 2; c <= Math.sqrt(candidate); ++c) {
        if (candidate % c === 0) {
          // not prime
          isPrime = false;
          break;
        }
      }
      if (isPrime) {
        primes.push(candidate);
      }
    }
    return primes;
  }

  function factorial(n) {
    if (n <= 1) {
      return 1;
      //recursive case
    } else {
      return n * factorial(n - 1);
    }
  }
  function long(n) {
    while (n > 0) {
      n--;
    }
  }

  function handleClick() {
    long(10000000000);
    result = "Done";
  }
</script>

<style>
			button {
			  background: #ff3e00;
			  color: white;
			  border: none;
			  padding: 8px 12px;
			  border-radius: 2px;
			  font-size: 22px;
			}
</style>

<button on:click={handleClick}>
  State: {result} 
</button>