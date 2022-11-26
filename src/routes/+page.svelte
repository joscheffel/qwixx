<script>
    import PunishRow from "../components/PunishRow.svelte";
    import ResultRow from "../components/ResultRow.svelte";
    import NumberRow from "../components/NumberRow.svelte";
    import DiceRow from "../components/DiceRow.svelte";
    import Button from "../components/Button.svelte";

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

    $: resetFlag = false;

    function reset() {
        if (resetFlag) {
            redRow.reset();
            yellowRow.reset();
            greenRow.reset();
            blueRow.reset();
            punishRow.reset();
            resetFlag = false;
        } else {
            resetFlag = true;
        }
    }

    function cancelReset() {
        resetFlag = false;
    }

    function help() {
        new Audio("help.mp3").play();
    }

    function repeat() {
        new Audio("repeat.mp3").play();
    }

    function ready() {
        new Audio("ready.mp3").play();
    }

    function end() {
        new Audio("end.mp3").play();
    }

    function beforeUnload(event) {
        console.log("something happend");
        // Cancel the event as stated by the standard.
        event.preventDefault();
        // Chrome requires returnValue to be set.
        event.returnValue = "Willst du wirklich die Seite verlassen? (Alle Eingaben werden verschwinden)";
        // more compatibility
        return '...';
    }

</script>

<svelte:window on:beforeunload={beforeUnload}/>


<svelte:head>
    <title>Home</title>
    <meta name="description" content="Svelte demo app"/>
</svelte:head>

{#if resetFlag}
    <div class="h-screen w-screen flex flex-col justify-around content-center fixed z-50 bg-white">
        <h1 class="text-2xl mt-auto ml-auto mr-auto">Willst du wirklich den Spielzettel zurücksetzen?</h1>
        <div class="mb-auto ml-auto mr-auto">
            <button type="button" class="text-white bg-green-500 h-20 w-20 rounded-2xl m-0.5 hover:bg-green-900" on:click={reset}>Ja</button>
            <button type="button" class="text-white bg-red-500 h-20 w-20 rounded-2xl m-0.5 hover:bg-red-900" on:click={cancelReset}>Nein</button>
        </div>
    </div>
{/if}

<section>
    <h1 class="text-5xl mb-5">Qwixx</h1>
    <DiceRow></DiceRow>
    <div class="rounded-2xl bg-gray-300 w-fit p-0.5 m-1 mt-8">
        <NumberRow bind:this={redRow} colorNumber="{0}" on:selects={handleSelects}></NumberRow>
        <NumberRow bind:this={yellowRow} colorNumber="{1}" on:selects={handleSelects}></NumberRow>
        <NumberRow bind:this={greenRow} colorNumber="{2}" reversed="{true}" on:selects={handleSelects}></NumberRow>
        <NumberRow bind:this={blueRow} colorNumber="{3}" reversed="{true}" on:selects={handleSelects}></NumberRow>
        <div class="flex flex-wrap">
            <button type="button" class="rounded-2xl text-4xl h-20 p-1 m-0.5 bg-gray-500 text-white hover:bg-gray-700"
                    on:click={reset}>Reset
            </button>
            <button type="button" class="rounded-2xl text-xs h-20 w-20 p-1 m-0.5 bg-red-500 text-white hover:bg-red-700"
                    on:click={help}>
                <svg class="fill-white h-10 w-10 m-auto" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
                    <!--! Font Awesome Pro 6.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
                    <path d="M256 0C114.6 0 0 114.6 0 256s114.6 256 256 256s256-114.6 256-256S397.4 0 256 0zM256 464c-114.7 0-208-93.31-208-208S141.3 48 256 48s208 93.31 208 208S370.7 464 256 464zM256 336c-18 0-32 14-32 32s13.1 32 32 32c17.1 0 32-14 32-32S273.1 336 256 336zM289.1 128h-51.1C199 128 168 159 168 198c0 13 11 24 24 24s24-11 24-24C216 186 225.1 176 237.1 176h51.1C301.1 176 312 186 312 198c0 8-4 14.1-11 18.1L244 251C236 256 232 264 232 272V288c0 13 11 24 24 24S280 301 280 288V286l45.1-28c21-13 34-36 34-60C360 159 329 128 289.1 128z"/>
                </svg>
            </button>
            <button type="button"
                    class="rounded-2xl text-xs h-20 w-20 p-1 m-0.5 bg-yellow-500 text-white hover:bg-yellow-700"
                    on:click={repeat}>
                <svg class="fill-white h-10 w-10 m-auto" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
                    <!--! Font Awesome Pro 6.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
                    <path d="M463.5 224H472c13.3 0 24-10.7 24-24V72c0-9.7-5.8-18.5-14.8-22.2s-19.3-1.7-26.2 5.2L413.4 96.6c-87.6-86.5-228.7-86.2-315.8 1c-87.5 87.5-87.5 229.3 0 316.8s229.3 87.5 316.8 0c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0c-62.5 62.5-163.8 62.5-226.3 0s-62.5-163.8 0-226.3c62.2-62.2 162.7-62.5 225.3-1L327 183c-6.9 6.9-8.9 17.2-5.2 26.2s12.5 14.8 22.2 14.8H463.5z"/>
                </svg>
            </button>
            <button type="button"
                    class="rounded-2xl text-xs h-20 w-20 p-1 m-0.5 bg-green-500 text-white hover:bg-green-700"
                    on:click={ready}>
                <svg class="fill-white h-10 w-10 m-auto" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
                    <!--! Font Awesome Pro 6.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
                    <path d="M470.6 105.4c12.5 12.5 12.5 32.8 0 45.3l-256 256c-12.5 12.5-32.8 12.5-45.3 0l-128-128c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0L192 338.7 425.4 105.4c12.5-12.5 32.8-12.5 45.3 0z"/>
                </svg>
            </button>
            <button type="button"
                    class="rounded-2xl text-xs h-20 w-20 p-1 m-0.5 bg-blue-500 text-white hover:bg-blue-700"
                    on:click={end}>
                <svg class="fill-white h-10 w-10 m-auto" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
                    <!--! Font Awesome Pro 6.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
                    <path d="M288 32c0-17.7-14.3-32-32-32s-32 14.3-32 32V256c0 17.7 14.3 32 32 32s32-14.3 32-32V32zM143.5 120.6c13.6-11.3 15.4-31.5 4.1-45.1s-31.5-15.4-45.1-4.1C49.7 115.4 16 181.8 16 256c0 132.5 107.5 240 240 240s240-107.5 240-240c0-74.2-33.8-140.6-86.6-184.6c-13.6-11.3-33.8-9.4-45.1 4.1s-9.4 33.8 4.1 45.1c38.9 32.3 63.5 81 63.5 135.4c0 97.2-78.8 176-176 176s-176-78.8-176-176c0-54.4 24.7-103.1 63.5-135.4z"/>
                </svg>
            </button>
            <PunishRow bind:this={punishRow} on:selects={handleSelects}></PunishRow>
        </div>
    </div>
    <ResultRow bind:this={resultRow} bind:selects={selects}></ResultRow>
    <div class="h-60">
    </div>
</section>
