<script>
    export let number = 0;
</script>

<div class="h-full w-full p-3 text-xs">
    {#if number === 1}
        <div class="h-1/3 flex flex-row justify-center content-center">
        </div>
        <div class="h-1/3 flex justify-center">
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-center content-center">
        </div>
    {:else if number === 2}
        <div class="h-1/3 flex flex-row justify-start content-center">
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-center content-center">
        </div>
        <div class="h-1/3 flex flex-row justify-end content-center">
            <p>●</p>
        </div>
    {:else if number === 3}
        <div class="h-1/3 flex flex-row justify-start content-center">
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-center content-center">
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-end content-center">
            <p>●</p>
        </div>
    {:else if number === 4}
        <div class="h-1/3 flex flex-row justify-between content-center">
            <p>●</p>
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-center content-center">
        </div>
        <div class="h-1/3 flex flex-row justify-between content-center">
            <p>●</p>
            <p>●</p>
        </div>
    {:else if number === 5}
        <div class="h-1/3 flex flex-row justify-between content-center">
            <p>●</p>
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-center content-center">
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-between content-center">
            <p>●</p>
            <p>●</p>
        </div>
    {:else if number === 6}
        <div class="h-1/3 flex flex-row justify-between content-center">
            <p>●</p>
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-between content-center">
            <p>●</p>
            <p>●</p>
        </div>
        <div class="h-1/3 flex flex-row justify-between content-center">
            <p>●</p>
            <p>●</p>
        </div>
    {/if}
</div>