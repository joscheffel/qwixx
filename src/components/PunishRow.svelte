<script>
    import Button from "./Button.svelte";
    import {createEventDispatcher} from "svelte";

    const dispatch = createEventDispatcher();

    $:buttons = [
        {bNumber: 1, clicked: false},
        {bNumber: 2, clicked: false},
        {bNumber: 3, clicked: false},
        {bNumber: 4, clicked: false},
    ]

    let oldSelects = 0;


    function handleClick() {
        let selects = 0;
        for (let i = 0; i < buttons.length; i++) {
            if (buttons[i].clicked) {
                selects += 1;
            }
        }
        dispatch('selects', {row: 4, selects: selects});
        console.log("Shout out a punish dice");

        if(oldSelects < selects) {
            let audio = new Audio('punish.mp3');
            audio.play();
        }
        oldSelects = selects;
    }

    export function reset() {
        for (let i = 0; i < buttons.length; i++){
            buttons[i].clicked = false;
        }
        handleClick();
    }
</script>

<div class="text-white text-4xl flex flex-wrap p-0.5 m-0.5 mb-2">
    <h1 class="text-3xl text-black mt-auto mb-auto mr-2">Fehlwürfe je -5</h1>
    {#each buttons as button}
            <Button bNumber="{button.bNumber}" bind:clicked="{button.clicked}"
                    colorNumber="{4}" on:message={handleClick}>-5</Button>
    {/each}
</div>