<script>
  // const [count,setCount] = useState(0)
  export let count = 0
  export let name = ""
  let  disabled = false 
  const increment = () => {
    // setState(count+1)
    count += 1
  }
</script>
<div>
<label for="">{name}</label>
<input type="checkbox" checked={disabled}>

<button {disabled} on:click={increment}>
  Clicks: {count}
</button>
<slot/>
</div>




<style>
  div{
    border: 2px solid #ff3e00;
    padding: 1rem;
  }
  button {
    font-family: inherit;
    font-size: inherit;
    padding: 1em 2em;
    color: #ff3e00;
    background-color: rgba(255, 62, 0, 0.1);
    border-radius: 2em;
    border: 2px solid rgba(255, 62, 0, 0);
    outline: none;
    width: 200px;
    font-variant-numeric: tabular-nums;
    cursor: pointer;
  }

  button:focus {
    border: 2px solid #ff3e00;
  }

  button:active {
    background-color: rgba(255, 62, 0, 0.2);
  }
</style>
