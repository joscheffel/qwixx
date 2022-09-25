<script>

    let pointsScale = [0, 1, 3, 6, 10, 15, 21, 28, 36, 45, 55, 66, 78];
    let showResult = false;

    // red, yellow, green, blue, punish
    export let selects;

    function toggleResults() {
        showResult = !showResult;
    }
</script>

<div class="mt-5 mb-5">
    <div class="flex flex-wrap mb-2">
        <div class="m-1 flex flex-col text-center">
            <h1 class="text-3xl text-gray-500 border-b-2 border-gray-500 p-1">Kreuze</h1>
            <h1 class="text-3xl text-gray-500">Punkte</h1>
        </div>
        {#each pointsScale as point, i}
            <div class="rounded-2xl border-2 border-gray-500 m-1 w-14 flex flex-col text-center">
                <h1 class="text-4xl text-gray-500 border-b-2 border-gray-500 pb-1">{i}</h1>
                <h1 class="text-4xl text-gray-500">{point}</h1>
            </div>
        {/each}
    </div>
    <div>
        <button type="button" class="text-white bg-emerald-400 rounded-2xl text-4xl p-2 m-2 hover:bg-emerald-600 h-20"
                on:click={() => toggleResults()}>Ergebnis anzeigen
        </button>
    </div>
    {#if showResult}
        <div class="m-4 flex flex-wrap">
            <div class="rounded-2xl border-2 border-red-500 w-28 h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-center text-4xl">{pointsScale[selects[0]]}</h1>
            </div>
            <div class="h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-4xl">+</h1>
            </div>
            <div class="rounded-2xl border-2 border-yellow-500 w-28 h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-center text-4xl">{pointsScale[selects[1]]}</h1>
            </div>
            <div class="h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-4xl">+</h1>
            </div>
            <div class="rounded-2xl border-2 border-green-500 w-28 h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-center text-4xl">{pointsScale[selects[2]]}</h1>
            </div>
            <div class="h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-4xl">+</h1>
            </div>
            <div class="rounded-2xl border-2 border-blue-500 w-28 h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-center text-4xl">{pointsScale[selects[3]]}</h1>
            </div>
            <div class="h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-4xl">-</h1>
            </div>
            <div class="rounded-2xl border-2 border-gray-500 w-28 h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-center text-4xl">{selects[4] * (5)}</h1>
            </div>
            <div class="h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-4xl">=</h1>
            </div>
            <div class="rounded-2xl border-2 border-gray-500 w-28 h-20 flex flex-col content-around justify-around m-2">
                <h1 class="text-center text-4xl">{pointsScale[selects[0]] + pointsScale[selects[1]] + pointsScale[selects[2]] + pointsScale[selects[3]] - selects[4] * 5}</h1>
            </div>
        </div>
    {/if}
</div>