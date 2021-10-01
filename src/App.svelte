<script>
import Formulario from './Formulario.svelte'
import Imagen from './Imagen.svelte'
import Header from './Header.svelte'
import Spinner from './Spinner.svelte'
let espera = false
 let promesa
 const api =  async (dato) => {
  const key = "23547014-a2604cbac9ac5f20f341a38e6";
  const url = ` https://pixabay.com/api/?key=${key}&q=${dato}&per_page=${"30"}&page=${"1"}`;
  const res = await fetch(url);
  const imagens = await res.json();
  return imagens.hits
};

const nueva = e =>{
   promesa = api(e.target.children[0].value)
   espera = true
}
 
 
</script>
<Header>

<Formulario on:submit={nueva} />
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
</style>
