<script>
    import Button from "./Button.svelte";
    import {createEventDispatcher, onMount} from "svelte";

    export let colorNumber = 0;
    export let reversed = false;
    let lockButtonNumber = 11;
    const dispatch = createEventDispatcher();

    let buttonsInitial = [
        {bNumber: 2, clicked: false},
        {bNumber: 3, clicked: false},
        {bNumber: 4, clicked: false},
        {bNumber: 5, clicked: false},
        {bNumber: 6, clicked: false},
        {bNumber: 7, clicked: false},
        {bNumber: 8, clicked: false},
        {bNumber: 9, clicked: false},
        {bNumber: 10, clicked: false},
        {bNumber: 11, clicked: false},
        {bNumber: 12, clicked: false},
        {bNumber: 13, clicked: false}
    ];

    let buttons

    if (reversed) {
        $:buttons = [...buttonsInitial].reverse();
        lockButtonNumber = 0;
    } else {
        $:buttons = [...buttonsInitial];
    }

    export function handleClicks() {
        let selects = 0;
        for (let i = 0; i < buttons.length; i++) {
            if (buttons[i].clicked) {
                selects += 1;
            }
        }
        dispatch('selects', {row: colorNumber, selects: selects});

    }

    function handleLockClick(){
        new Audio('color' + colorNumber + '.mp3').play();
        setTimeout(
            () => {new Audio("zu.mp3").play();},
            500
        )
        handleClicks();
    }

    export function reset() {
        for (let i = 0; i < buttons.length; i++) {
            buttons[i].clicked = false;
        }
        handleClicks();
    }
</script>

<div class="text-white text-4xl flex flex-wrap p-0.5 ml-0.5 mb-2">
    {#each buttons as button, i}
        {#if button.bNumber !== 13}
            <Button bNumber="{button.bNumber}" bind:clicked="{button.clicked}"
                    colorNumber="{colorNumber}" on:message={handleClicks}>{button.bNumber}</Button>
        {/if}
    {/each}

    <Button bNumber="{buttons[lockButtonNumber].bNumber}" bind:clicked="{buttons[lockButtonNumber].clicked}"
            colorNumber="{colorNumber}" on:message={handleLockClick}>
        <svg class="fill-white h-10 w-10 m-auto" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
            <!--! Font Awesome Pro 6.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
            <path d="M144 144v48H304V144c0-44.2-35.8-80-80-80s-80 35.8-80 80zM80 192V144C80 64.5 144.5 0 224 0s144 64.5 144 144v48h16c35.3 0 64 28.7 64 64V448c0 35.3-28.7 64-64 64H64c-35.3 0-64-28.7-64-64V256c0-35.3 28.7-64 64-64H80z"/>
        </svg>
    </Button>
</div>