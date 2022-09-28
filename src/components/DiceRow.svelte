<script>

    import Button from "./Button.svelte";
    import Dice from "./Dice.svelte";

    let diceWhiteOne = 0;
    let diceWhiteTwo = 0;
    let diceRed = 0;
    let diceYellow = 0;
    let diceGreen = 0;
    let diceBlue = 0;

    function dice() {
        return Math.floor(Math.random() * 6 + 1);
    }

    function showDices() {
        diceWhiteOne = dice();
        diceWhiteTwo = dice();
        diceRed = dice();
        diceYellow = dice();
        diceGreen = dice();
        diceBlue = dice();
    }
</script>

<div class="flex justify-start content-center">
    <button type="button" class="rounded-2xl text-4xl h-20 p-1 m-2 mt-0 bg-gray-500 text-white hover:bg-gray-700" on:click={showDices}>Würfeln
    </button>
    <Dice bind:number="{diceWhiteOne}" colorNumber="{4}"></Dice>
    <Dice bind:number="{diceWhiteTwo}" colorNumber="{4}"></Dice>
    <Dice bind:number="{diceRed}" colorNumber="{0}"></Dice>
    <Dice bind:number="{diceYellow}" colorNumber="{1}"></Dice>
    <Dice bind:number="{diceGreen}" colorNumber="{2}"></Dice>
    <Dice bind:number="{diceBlue}" colorNumber="{3}"></Dice>
</div>