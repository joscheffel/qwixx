<script>
    import {createEventDispatcher} from "svelte";

    export let bNumber;
    export let clicked = false;
    export let disableClick = false;
    export let colorNumber = 0;

    const dispatch = createEventDispatcher();

    function handleClick(buttonNumber) {
        clicked = !clicked;
        dispatch('message',{});
    }
</script>


{#if clicked && !disableClick}
    <button type="button" class="bg-black h-20 w-20 rounded-2xl m-0.5 ml-0"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 0}
    <button type="button" class="text-white bg-red-500 h-20 w-20 rounded-2xl m-0.5 ml-0 hover:bg-red-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 1}
    <button type="button" class="text-white bg-yellow-500 h-20 w-20 rounded-2xl m-0.5 ml-0 hover:bg-yellow-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 2}
    <button type="button" class="text-white bg-green-500 h-20 w-20 rounded-2xl m-0.5 ml-0 hover:bg-green-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 3}
    <button type="button" class="text-white bg-blue-500 h-20 w-20 rounded-2xl m-0.5 ml-0 hover:bg-blue-900"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{:else if colorNumber === 4}
    <button type="button" class="text-white bg-white h-20 w-20 rounded-2xl m-0.5 ml-0 hover:bg-gray-500 border-gray-500 border-2"
            on:click={() => handleClick(bNumber)}>
        <slot></slot>
    </button>
{/if}