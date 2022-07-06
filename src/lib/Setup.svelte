<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    
    export let cardSize = 3;
    export let numberOfCards = 10;
    export let bingoValues;
    export let uniqueBingoValues;
    const generate = () => dispatch('generate');
    
</script>

<div class="wrapper">
    <div class="inputs">
            <div>
                <h3 class="label">#</h3>
                <input type="number" placeholder="# Cards" bind:value={numberOfCards}/>
            </div>
            <div >
                <h3 class="label">Size</h3>
                <input type="number" placeholder="Card size" bind:value={cardSize}/>
            </div>
        <button on:click={generate}>Generate</button>
    </div>
    <h3>{numberOfCards} cards: {cardSize} x {cardSize}</h3>
    <div class="textareas">
        <div>
            <h2>Bingos</h2>
            <textarea class="bingos" bind:value={bingoValues}/>
        </div>
        <div>
            <h2>Unique</h2>
            <textarea class="unique" bind:value={uniqueBingoValues}/>
        </div>
    </div>
</div>

<style>
    .wrapper {
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
        margin: auto;
        row-gap: 1em;
    }

    .textareas {
        display: flex;
        column-gap: 2em;
    }

    .inputs {
        display: flex;
        column-gap: 1em;
    }

    .label {
        margin: 0;
    }

    input {
        height: 3em;
        width: 3em;
        border-radius: 5px;
        border: 2px solid rgb(132, 101, 15);
        color: rgb(132, 101, 15);
        text-align: center;
        font-weight: 600;
        font-size: 1.1em;
    }

    textarea {
        width: 30vw;
        height: 50vh;
        border-radius: 5px;   
        border: 2px solid rgb(132, 101, 15);
    }


</style>
