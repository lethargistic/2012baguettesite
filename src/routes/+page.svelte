<script lang="ts">
    import roach from '$lib/assets/roach.gif'
    import skel from '$lib/assets/skeleton-trumpet.gif'
    import baguette from '$lib/assets/baguette.png'
    import {Tween} from "svelte/motion";

    let baguettePos = new Tween(-200);

    let click = $state(false);
    let chinese = true;
</script>

<main>
    {#each Array.from({length: 4}) as _, i (i)}
        <marquee>breadsite</marquee>
    {/each}

    <img class="roach" src={roach} alt="roach">
    <img class="skel" src={skel} alt="skeleton doot doot">
    <img class="baguette" style={`top: ${baguettePos.current}px`} src={baguette} alt="baguette">

    {#if click}
        <div class="baguette-button-cont">
            <button onclick={() => baguettePos.target = 500}>
                {#if chinese}
                    法棍
                {:else}
                    baguette
                {/if}
            </button>
        </div>
    {/if}
</main>

<svelte:window onclick={() => click = true}/>

<style>
    .baguette {
        position: absolute;
        width: 20vw;
        top: -200px;
        transform: translate(-50%, -50%);

    }

    .roach {
        width: 70px;
        margin-left: -1vw;
    }

    .skel {
        position: relative;
        width: 80px;
        left: 200px;
        top: 280px;
    }

    .baguette-button-cont {
        width: 100%;
        display: grid;
        place-content: center;

        & button {
            width: 100px;
        }
    }

    main {
        margin-top: 10vh;
        width: 20vw;
        height: 70vh;
        background: white;
    }

    :global {
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            display: flex;
            justify-content: center;
            background: url("/stars1.gif");
        }
    }
</style>