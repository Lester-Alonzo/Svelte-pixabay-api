<script>
    import {scale, fade} from 'svelte/transition'
    export let imagenes 
</script>

    <div class="contenido">
        {#each imagenes as item}
             <!-- content here -->
             <div class="card" in:scale out:fade>
             <img src={item.previewURL} alt="img">
             <a href={item.largeImageURL} target="_balnk">Ver Imagen</a>
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
        margin: 0 auto;
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
        width: 30%;
        margin:1rem  auto;
        padding: 1rem;
        border-radius: 1rem;
        background-color: rgb(32, 32, 32);
        box-shadow: 1px 1px 9px rgba(0, 0, 0, 0.493);
        text-decoration: none;
        cursor: pointer;
        font-weight: bold;
    }
    .card a:hover{
        background-color: yellowgreen;
    }
    @media screen and (max-width:600px){
        .contenido{
            grid-template-columns: 1fr;
        }
    }
</style>