<script>
import { onMount } from "svelte";
const key = "23547014-a2604cbac9ac5f20f341a38e6";
  const url =  ` https://pixabay.com/api/?key=${key}&q=${'anime'}&per_page=${'30'}&page=${'1'}`
  
  onMount(async () => {
    const res = await fetch(url)
    const imagen = res.json()
    console.log(imagen);
  })
</script>
<h1>Inicio</h1>