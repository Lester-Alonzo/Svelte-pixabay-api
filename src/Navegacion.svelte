<script>
export let quitar
export let sumar 
</script>

<div class="navegac">
    <button type="button" on:click={quitar}>Anterior</button>
    <button type="button" on:click={sumar}>Siguiente</button>
</div>

<style>
    .navegac{
        text-align: center;
    }
    button{
        border: none;
        background-color: rgb(32, 32, 32);
        padding: 1em;
        margin-left: 1em;
        margin-top: 1rem;
        color: white;
        border-radius: 1rem;
    }
button:active{
        background-color: yellowgreen;
    }
</style>