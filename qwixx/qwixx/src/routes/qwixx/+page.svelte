<script>
    import PunishRow from "../../components/PunishRow.svelte";
    import ResultRow from "../../components/ResultRow.svelte";
    import NumberRow from "../../components/NumberRow.svelte";
    import DiceRow from "../../components/DiceRow.svelte";

    let redRow;
    let yellowRow;
    let greenRow;
    let blueRow;
    let punishRow;
    let resultRow;

    // red, yellow, green, blue, punish
    $:selects = [0, 0, 0, 0, 0];

    function handleSelects(event) {
        selects[event.detail.row] = event.detail.selects;
    }

    function reset() {
        redRow.reset();
        yellowRow.reset();
        greenRow.reset();
        blueRow.reset();
        punishRow.reset();
    }
</script>

<svelte:head>
    <title>Home</title>
    <meta name="description" content="Svelte demo app"/>
</svelte:head>

<section>
    <h1 class="text-5xl mb-5">Qwixx</h1>
    <DiceRow></DiceRow>
    <div class="rounded-2xl bg-gray-300 w-fit p-2 m-1">
        <NumberRow bind:this={redRow} colorNumber="{0}" on:selects={handleSelects}></NumberRow>
        <NumberRow bind:this={yellowRow} colorNumber="{1}" on:selects={handleSelects}></NumberRow>
        <NumberRow bind:this={greenRow} colorNumber="{2}" reversed="{true}" on:selects={handleSelects}></NumberRow>
        <NumberRow bind:this={blueRow} colorNumber="{3}" reversed="{true}" on:selects={handleSelects}></NumberRow>
        <div class="flex justify-between">
            <button type="button" class="rounded-2xl text-4xl h-20 p-1 m-2 bg-gray-500 text-white hover:bg-gray-700" on:click={reset}>Reset
            </button>
            <PunishRow bind:this={punishRow} on:selects={handleSelects}></PunishRow>
        </div>
    </div>
    <ResultRow bind:this={resultRow} bind:selects={selects}></ResultRow>
</section>
