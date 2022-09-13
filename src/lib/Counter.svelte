<script>
  let count = 0
  const increment = () => {
    count += 1
  }

  const decrement = () => {
    count -= 1
  }

  $: isDisabledMin = count <= 0
</script>

<div class="wrapper">
  <button on:click={increment}>
    Increment
  </button>
  <button on:click={decrement} disabled={isDisabledMin}>
    Decrement
  </button>
</div>
<div>
  Count: {count}
</div>
<div>
  Count + 1: {count + 1}
</div>

<style>
  .wrapper {
    display: flex;
    justify-content: space-between;

  }
</style>
