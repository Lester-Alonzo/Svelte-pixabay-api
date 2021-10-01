<script>
import { onMount } from "svelte";
import Formulario from './Formulario.svelte'
import Imagen from './Imagen.svelte'
let resul = []
let ep = spera()
let busqueda= ''
 async function spera(){ 
const key = "23547014-a2604cbac9ac5f20f341a38e6";
  const url =  ` https://pixabay.com/api/?key=${key}&q=${'anime'}&per_page=${'30'}&page=${'1'}`
    const res = await fetch(url)
    const imagen = await res.json()    
    return imagen.hits
   
 }
 const nueva = e => {
     busqueda = e.target.children[0].value
    consulta()
 }
 
</script>
<Formulario on:submit={nueva}/>

{#await ep}
  <!-- consulta is pending -->
  <h1>Cargando</h1>
{:then imagen}
  <Imagen imagenes={imagen}/>
 {:catch error}
  <!-- consulta was rejected -->
  <h2>Error:{error}</h2>
{/await}
