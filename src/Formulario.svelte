<script>


</script>
<form action="" on:submit|preventDefault>
    <input type="text" name="busqueda" placeholder="Ingresa una busqueda"> 
    <button type="submit">Buscar</button>       
</form>

<style>
    input{
        outline: none;
        background: transparent;
        border: none;
        border-bottom: 3px solid white;
        color: white;
        text-align: center;
    }
    input:focus{
        border-bottom:4px solid yellowgreen;
        color: yellowgreen;
    }

    button{
        border: none;
        background-color: rgb(32, 32, 32);
        padding: 1em;
        margin-left: 1em;
        color: white;
        border-radius: 1rem;
    }
    button:active{
        background-color: yellowgreen;
    }
    @media screen and (max-width:600px){
        form{
            text-align: center;
        }
    }
</style>