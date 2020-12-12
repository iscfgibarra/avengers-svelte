<script>
    import { store } from "../store";
    import { fade } from "svelte/transition";

    function closeSnackbar() {
        store.update((state) => ({
            ...state,
            show: null,
            type: null,
            title: null,
        }));
    }
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

    .snackbar-container {
        display: flex;
        flex-direction: row;
        padding: 15px;
    }

    span {
        color: var(--white);
        flex-grow: 3;
        font-size: 12px;
        user-select: none;
    }
    .close {
        flex-grow: 1;
        text-align: right;
        cursor: pointer;
        color: var(--white);
        font-size: 1rem;
        user-select: none;
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
