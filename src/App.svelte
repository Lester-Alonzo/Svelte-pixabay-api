<script>
import Formulario from './Formulario.svelte'
import Imagen from './Imagen.svelte'
import Header from './Header.svelte'
import Spinner from './Spinner.svelte'
import Navegacion from './Navegacion.svelte'
let espera = false
 let promesa
 let busquedaG
 let filtro
let fil
let paginas
let count = 1
 const api =  async (dato, fil, count) => {
  const key = "23547014-a2604cbac9ac5f20f341a38e6";
  const url = ` https://pixabay.com/api/?key=${key}&q=${dato}&per_page=${"50"}&page=${count}&order=${fil}`;
  const res = await fetch(url);
  const imagens = await res.json();
  paginas = imagens.totalHits / 50
  return imagens.hits
};

const nueva = e =>{
   busquedaG = e.target.children[0].value
   promesa = api(e.target.children[0].value, fil)
   espera = true
}
const cambio = e =>{
  filtro = e.target.value
   promesa = api(busquedaG, e.target.value)
} 
const quitar = e =>{
  if (count <= 1) {
  }else{
    count -= 1
   promesa =  api(busquedaG, filtro, count )
  }
}
const sumar = e =>{
  if (count >= paginas) {
    
  }else{
    count += 1
   promesa = api(busquedaG, filtro, count)
  }
}
</script>
<Header>
<div class="change">
<Formulario on:submit={nueva} />
<div class="filtro" on:change={cambio}>
  <div><input type="radio" bind:group={fil} value="popular"> <span>popular</span> </div>
  <div><input type="radio" bind:group={fil} value="latest"> <span>latest</span></div>
</div>
</div>

</Header>
<div class="contenedor">
{#if espera}
   <!-- content here -->
   {#await promesa}
     <!-- promise is pending -->
     <Spinner/>
   {:then valor}
     <!-- promise was fulfilled -->
    <Imagen imagenes={valor}/>
   {:catch error}
     <!-- promise was rejected -->
     <h2>{error}</h2>
   {/await}

<Navegacion quitar={quitar} sumar={sumar}/>
{:else}
   <!-- else content here -->
   <span>Realiza una busqueda</span>
{/if}
</div>

<style>
  span, h2{
    display: block;
    color: white;
    text-align: center;
  }
  .contenedor{
    margin: auto;
    /* border: 1px solid greenyellow; */
  }

  .filtro{
    display: flex;
    justify-content: space-around;
  }


  @media screen and (max-width:600px){

  }
</style>
