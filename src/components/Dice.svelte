<script>
    import DiceNumber from "./DiceNumber.svelte";

    export let colorNumber = 0;
    export let number = 0;
    export let notSmall = true;

</script>

{#if notSmall}
    {#if colorNumber === 0}
        <div class="text-white border-2 border-red-500 bg-red-500 h-20 w-20 rounded-2xl m-0.5">
            <DiceNumber bind:number={number}></DiceNumber>
        </div>
    {:else if colorNumber === 1}
        <div class="text-white border-2 border-yellow-500 bg-yellow-500 h-20 w-20 rounded-2xl m-0.5">
            <DiceNumber bind:number={number}></DiceNumber>
        </div>
    {:else if colorNumber === 2}
        <div class="text-white border-2 border-green-500 bg-green-500 h-20 w-20 rounded-2xl m-0.5">
            <DiceNumber bind:number={number}></DiceNumber>
        </div>
    {:else if colorNumber === 3}
        <div class="text-white border-2 border-blue-500 bg-blue-500 h-20 w-20 rounded-2xl m-0.5">
            <DiceNumber bind:number={number}></DiceNumber>
        </div>
    {:else}
        <div class="text-black border-2 border-black bg-white h-20 w-20 rounded-2xl m-0.5">
            <DiceNumber bind:number={number}></DiceNumber>
        </div>
    {/if}
{:else}
    {#if colorNumber === 0}
        <div class="text-white border-2 border-red-500 bg-red-500 h-6 w-6 rounded-[4px] m-0.5 flex justify-center content-center">
            <h1 class="text-xs pt-0.5">{number}</h1>
        </div>
    {:else if colorNumber === 1}
        <div class="text-white border-2 border-yellow-500 bg-yellow-500 h-6 w-6 rounded-[4px] m-0.5 flex justify-center content-center">
            <h1 class="text-xs pt-0.5">{number}</h1>
        </div>
    {:else if colorNumber === 2}
        <div class="text-white border-2 border-green-500 bg-green-500 h-6 w-6 rounded-[4px] m-0.5 flex justify-center content-center">
            <h1 class="text-xs pt-0.5">{number}</h1>
        </div>
    {:else if colorNumber === 3}
        <div class="text-white border-2 border-blue-500 bg-blue-500 h-6 w-6 rounded-[4px] m-0.5 flex justify-center content-center">
            <h1 class="text-xs pt-0.5">{number}</h1>
        </div>
    {:else}
        <div class="text-black border-2 border-black bg-white h-6 w-6 rounded-[4px] m-0.5 flex justify-center content-center ">
            <h1 class="text-xs pt-0.5">{number}</h1>
        </div>
    {/if}
{/if}