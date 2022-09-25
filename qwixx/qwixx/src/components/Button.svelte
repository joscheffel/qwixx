<script>
    import {createEventDispatcher} from "svelte";

    export let bNumber;
    export let clicked = false;
    export let colorNumber = 0;

    const dispatch = createEventDispatcher();

    function handleClick(buttonNumber) {
        clicked = !clicked;
        dispatch('message',{});
    }
</script>


{#if clicked}
    <button type="button" class="bg-black h-20 w-20 rounded-2xl m-0.5"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 0}
    <button type="button" class="bg-red-500 h-20 w-20 rounded-2xl m-0.5 hover:bg-red-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 1}
    <button type="button" class="bg-yellow-500 h-20 w-20 rounded-2xl m-0.5 hover:bg-yellow-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 2}
    <button type="button" class="bg-green-500 h-20 w-20 rounded-2xl m-0.5 hover:bg-green-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 3}
    <button type="button" class="bg-blue-500 h-20 w-20 rounded-2xl m-0.5 hover:bg-blue-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 4}
    <button type="button" class="bg-white h-20 w-20 rounded-2xl m-0.5 hover:bg-gray-500 border-gray-500 border-2"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{/if}