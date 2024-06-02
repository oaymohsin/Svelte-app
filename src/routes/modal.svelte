<script>

    export let message="default Message";
    export let showModal=false;
    let promo=false;

</script>

<div class="modal" class:promo={promo}  on:click>
    {#if showModal}
    <h3> {message}</h3>
    {/if}
</div>

<style>

    .promo {
        background-color: crimson;
        color: white;
       padding: 10px 20px;
       border-radius: 10px;
       font-size: small;
       font-weight: lighter;
    }
</style>