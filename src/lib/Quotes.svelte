<script>
  async function getRamdonQuote() {
    const res = await fetch("https://programming-quotes-api.herokuapp.com/quotes/random") 
    if (res.ok) {
      return await res.json()
    }
    throw new  Error(res.statusText)  

  }
  let quotePromise2 = getRamdonQuote() 
  let quotePromise = getRamdonQuote() 

</script>
  {#await quotePromise}
    <p>cargando...</p>
  {:then data}
    <p>{data.en}</p>
    <p>{data.author}</p>
  {:catch err}
  <p style="color:red;">{err}</p>
  {/await}
  <hr>
  {#await quotePromise2}
    <p>cargando...</p>
  {:then data}
    <p>{data.en}</p>
    <p>{data.author}</p>
  {:catch err}
  <p style="color:red;">{err}</p>
  {/await}