<script>
  let count = 0
  const increment = () => {
    count += 1
  }

  const decrement = () => {
    count -= 1
  }
</script>

<div class="wrapper">
  <button on:click={increment}>
    Increment
  </button>
  <button on:click={decrement}>
    Decrement
  </button>
</div>
<div>
  Count: {count}
</div>

<style>
  .wrapper {
    display: flex;
    justify-content: space-between;
  }
</style>
