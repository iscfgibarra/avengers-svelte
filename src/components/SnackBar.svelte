<script>
    import { store } from "../store";
    import { fade } from "svelte/transition";
</script>

<style>
    .snackbar {
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        z-index: 10;
        font-family: var(--font-family);
    }

    .success {
        background: var(--sucess);
    }

    .error {
        background: var(--error);
    }
</style>

<div>
    {#if $store.show}
        <div class="snackbar" transition:fade on:click={closeSnackbar}>
            <div class={`${$store.type} snackbar-container`}>
                <span>{$store.title}</span>
                <i class="fas fa-times close" />
            </div>
        </div>
    {/if}
</div>
