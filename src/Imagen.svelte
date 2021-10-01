<script>
    export let imagenes 
    console.log(imagenes);
</script>

    <div class="contenido">
        {#each imagenes as item}
             <!-- content here -->
             <div class="card">
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
        border: 1px solid pink;
    }
    .card{
        width: 80%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        border: 1px solid red;
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
    }
</style>