<script>
  export let message;
  export let index;
  export let removeHandler;
</script>

<li class="item">
  <span>Number {index + 1}: {message}</span>
  <button on:click={() => removeHandler(index)} class="remove_btn">Remove</button>
</li>

<style>
  .item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 5px 0;
  }

  .remove_btn {
    background-color: orangered;
    padding: 2px;
    color: #ffffff;
    font-size: 14px;
  }
</style>
