<script>
    import viewport from "./useViewportAction.js";
    import {fade} from "svelte/transition";
    import Dice from "./Dice.svelte";

    let diceWhiteOne = 0;
    let diceWhiteTwo = 0;
    let diceRed = 0;
    let diceYellow = 0;
    let diceGreen = 0;
    let diceBlue = 0;
    $: isSmall = false;

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

        let number = diceWhiteOne + diceWhiteTwo;
        let randomNumber = Math.floor(Math.random() * 15);

        if(randomNumber === 1){
            new Audio("amazing.mp3").play();
            setTimeout(
                () => {new Audio(number + '.mp3').play();},
                700
            )
        }else if(randomNumber === 2){
            new Audio("incredible.mp3").play();
            setTimeout(
                () => {new Audio(number + '.mp3').play();},
                900
            )
        }else if(randomNumber === 3){
            new Audio("magnificent.mp3").play();
            setTimeout(
                () => {new Audio(number + '.mp3').play();},
                1000
            )
        }else {
            let audio = new Audio(number + '.mp3');
            audio.play();
        }
    }
</script>

<div
        use:viewport
        on:enterViewport={() => isSmall = false}
        on:exitViewport={() => isSmall = true}
        class="flex justify-start content-center">
    <button type="button" class="rounded-2xl text-4xl h-20 p-1 m-2 mt-0 bg-gray-500 text-white hover:bg-gray-700"
            on:click={showDices}>Würfeln
    </button>
    <Dice bind:number="{diceWhiteOne}" colorNumber="{4}"></Dice>
    <Dice bind:number="{diceWhiteTwo}" colorNumber="{4}"></Dice>
    <Dice bind:number="{diceRed}" colorNumber="{0}"></Dice>
    <Dice bind:number="{diceYellow}" colorNumber="{1}"></Dice>
    <Dice bind:number="{diceGreen}" colorNumber="{2}"></Dice>
    <Dice bind:number="{diceBlue}" colorNumber="{3}"></Dice>
</div>

{#if isSmall}
    <div class="fixed top-0 flex bg-gray-300 w-fit rounded-b-[4px]" in:fade out:fade>
        <Dice bind:number="{diceWhiteOne}" colorNumber="{4}" notSmall="{!isSmall}"></Dice>
        <Dice bind:number="{diceWhiteTwo}" colorNumber="{4}" notSmall="{!isSmall}"></Dice>
        <Dice bind:number="{diceRed}" colorNumber="{0}" notSmall="{!isSmall}"></Dice>
        <Dice bind:number="{diceYellow}" colorNumber="{1}" notSmall="{!isSmall}"></Dice>
        <Dice bind:number="{diceGreen}" colorNumber="{2}" notSmall="{!isSmall}"></Dice>
        <Dice bind:number="{diceBlue}" colorNumber="{3}" notSmall="{!isSmall}"></Dice>
    </div>
{/if}