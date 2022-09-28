<script>
    import PunishRow from "../components/PunishRow.svelte";
    import ResultRow from "../components/ResultRow.svelte";
    import NumberRow from "../components/NumberRow.svelte";
    import DiceRow from "../components/DiceRow.svelte";

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
    <div class="flex flex-col justify-center content-center w-1/2">
        <h1 class="text-5xl m-auto">Alles Gute Zum Geburtstag</h1>
        <div class="m-auto">
            <script src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"></script>
            <lottie-player src="https://assets1.lottiefiles.com/packages/lf20_bXWwgY.json" background="transparent"
                           speed="1" style="width: 700px; height: 700px;" loop autoplay></lottie-player>
        </div>
        <a class="rounded-2xl border-2 border-emerald-500 text-black text-4xl m-auto p-2 text-center w-1/2 hover:bg-emerald-500 hover:text-white"
           href="/qwixx">Öffne das Geschenk</a>
    </div>
</section>
