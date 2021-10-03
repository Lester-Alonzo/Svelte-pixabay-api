<script>

</script>

<header class="contenido">
    <slot><!-- optional fallback --></slot>
</header>

<style>
    .contenido{
        height: 9rem;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 4em;
        border-radius: 1rem;
        box-shadow:1px 1px 9px rgba(0, 0, 0, 0.493);
        background-color: rgb(43, 43, 43);
        position:sticky;
        top: 2px;
    }
    @media screen and (max-width:600px){
        .contenido{
            height: 11rem;
        }
    }
</style>