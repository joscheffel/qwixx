<script>
</script>

<svelte:head>
    <title>Home</title>
    <meta name="description" content="Svelte demo app"/>
</svelte:head>

<section>
    <a href="/qwixx">
        <div class="flex flex-col justify-center content-center w-1/2">
            <h1 class="text-5xl m-auto mb-1">Alles Gute Zum Geburtstag</h1>
            <div class="m-auto mt-1">
                <script src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"></script>
                <lottie-player src="https://assets1.lottiefiles.com/packages/lf20_bXWwgY.json" background="transparent"
                               speed="0.7" style="width: 600px; height: 600px;" loop autoplay></lottie-player>
            </div>
            <a class="rounded-2xl border-2 border-emerald-500 text-black text-4xl m-auto p-2 text-center w-1/2 hover:bg-emerald-500 hover:text-white"
               href="/qwixx">Öffne Mich</a>
        </div>
    </a>

</section>
