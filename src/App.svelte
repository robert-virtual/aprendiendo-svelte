<script>
  let x = 0
  let y = 0
  let menuX = 0
  let menuY = 0
  let dragY = 0
  let dragX = 0
  document.addEventListener("mousemove",mouseMove)
  document.addEventListener("click",clickOut)
  function clickOut({target}) {
   if (target.id != "menuContext") {
    menu = false  
   }
  }
  function mouseMove({clientX,clientY}){
    x = clientX
    y = clientY
    if (moving) {
      dragX = clientX 
      dragY = clientY 
    }

  }
  let count = 0
  let menu = false
  let menucontext = (e)=>{
    let {clientX,clientY} = e
    console.log(clientX,clientY);
    if (clientY > 425) {
      clientY = 425 
    }
    menuX = clientX
    menuY = clientY
    e.preventDefault()
    menu = true

  }
  let moving = false
  function mouseDown({}) {
   moving = true 
  }
  function mouseUp({}) {
   moving = false 
  }
</script>

<main>
  <p on:click={()=>count += 2}>count:{count}</p>
  <div style="transform: translate({x}px,{y}px);" class="circle"></div>
  <div on:contextmenu={menucontext} class="square"></div>
  <div style="transform: translate({dragX}px,{dragY}px)" on:mousedown={mouseDown} on:mouseup={mouseUp} class="drag">
    <p>grag me</p>
  </div>
  
  {#if menu}
  <div  id="menuContext" style="transform: translate({menuX}px,{menuY}px);" class="menuContext">
    <button on:click={()=>console.log('btn Guardar')}>Guardar</button>
    <button>Editar</button>
    <button>Compartit</button>
  </div>
  {/if }
</main>

<style>
  .drag{
    background-color: #ff3e00;
    border: 1px white solid;
    color:white;
    position: absolute;
    top: 0;
    left: 0;
    padding: 0.5rem;
    height: 300px;
    cursor: move;
    width: 200px;
    z-index: 1000;
  }
  .menuContext::-webkit-scrollbar-thumb{
    width: 0.25rem;
    border-radius: 0.25rem;
    background-color: rgb(197, 197, 197);

  }
  .menuContext::-webkit-scrollbar-track{
    background-color: white;
    width: 0.25rem;
    border-radius: 0.25rem;
  }
  .menuContext::-webkit-scrollbar{
    background-color: white;
    border-radius: 0.25rem;
    width: 0.25rem;
  }
  .menuContext{
    overflow-y: scroll;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    position: absolute;
    background-color:white ;
    top: 0;
    left: 0;
    padding: 0.5rem;
    height: 300px;
    width: 200px;
    border-radius: 0.5rem;
    box-shadow: 0 0 6px gray;
    z-index: 999;
  }
  .square{
    position: absolute;
    top: 0;
    left: 0;
    width: 300px;
    height: 100vh;
    background-color: #ff3e00;
  }
  .circle{
    position: absolute;
    top: 0;
    left: 0;
    width: 100px;
    height: 100px;
    background-color: #ff3e00;
    border-radius: 50%;
  }
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }
</style>
