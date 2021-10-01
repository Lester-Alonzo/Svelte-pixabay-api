<script>
    import {scale, fade} from 'svelte/transition'
    export let imagenes 
    console.log(imagenes);
</script>

    <div class="contenido">
        {#each imagenes as item}
             <!-- content here -->
             <div class="card" in:scale out:fade>
             <img src={item.previewURL} alt="img">
             <a href={item.largeImageURL} target="_balnk">Ver en sitio</a>
             </div>
        {/each}
    </div>
<style>
    .contenido{
        display: grid;
        gap: 1rem;
        grid-template-columns: repeat(3, 1fr);
        text-align: center;
    }
    .card{
        width: 70%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        background-color: rgb(43, 43, 43);
        box-shadow: 1px 1px 9px rgba(0, 0, 0, 0.493);
        padding: 1rem;
        border-radius: 1rem;
        text-align: center;
    }
    .card img{
        max-width: 100%;
        border-radius: 1rem;
    }
    .card a{
        color: white;
        border: 1px solid red;
        width: 30%;
        margin: auto;
        padding: 1rem;
        border-radius: 1rem;
        background-color: gray;
        text-decoration: none;
        cursor: pointer;
    }
</style>