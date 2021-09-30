<script>
import { onMount } from "svelte";
import Formulario from './Formulario.svelte'
const key = "23547014-a2604cbac9ac5f20f341a38e6";
let i
let busqueda= ''
  const url =  ` https://pixabay.com/api/?key=${key}&q=${busqueda}&per_page=${'30'}&page=${'1'}`
 const consulta = async () =>{ 
    const res = await fetch(url)
    const imagen = await res.json()    
     return imagen
 }
 const nueva = e => {
     busqueda = e.target.children[0].value
 }
 
</script>
{#await consulta()}


    <Formulario on:submit={nueva}/>
