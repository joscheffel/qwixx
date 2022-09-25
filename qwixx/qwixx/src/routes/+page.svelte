<script>
    let clickCount = 0;

    function handleClick(){
        clickCount += 1;
    }
</script>

<svelte:head>
    <title>Home</title>
    <meta name="description" content="Svelte demo app"/>
</svelte:head>

<section>
    <h1>A Test for something</h1>
    <div class="text-white text-5xl flex flex-wrap justify-between">
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>1</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>2</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>3</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>4</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>5</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>6</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>7</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>8</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>9</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>10</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>11</button>
        <button type="button" class="bg-blue-500 h-40 w-40 rounded-2xl" on:click={handleClick}>12</button>
    </div>
    <h1 class="text-4xl">Number of clicks is: {clickCount}</h1>
</section>
