<script lang="ts">
    export let id: number;
    export let size: number = 3;
    export let squares: number = 9;
    export let values: string[];
</script>

<div class="card-wrapper">
    <div class="card-header">
        <img src={'/assets/diamond-gold-AE.png'} class="AE-logo" alt="AE-logo"/>
        <h2>#{id}</h2>
        <img src={'/assets/leaf.png'} class="leaf" alt="AE-leaf"/>
    </div>
    <div class="card" style="--grid-size: {size}">
        {#each Array(squares) as square, i}
            <div class="square">
                {values[i]}
            </div>
        {/each}
    </div>
</div>


<style>

    .card-wrapper {
        display: flex;
        flex-direction: column;
    }

    .card-header {
        display: grid;
        grid-template-columns: 2cm 1fr 2cm;
        width: 10cm;
        margin: auto;
    }

    .card {
        display: grid;
        grid-template-columns: repeat(var(--grid-size), calc(10cm / var(--grid-size)));
        grid-template-rows: repeat(var(--grid-size),  calc(10cm / var(--grid-size)));
        column-gap: 0px;
        row-gap: 0px;
        width: fit-content;
        height: fit-content;
        border: 3px solid rgb(132, 101, 15);
        border-collapse: separate;
        border-spacing: 0px 0px;
        padding: 0px;
        margin: auto;
    }

    .square {
        border: 1px solid rgb(132, 101, 15);
        font-size: 0.75em;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        color: rgb(132, 101, 15);
        font-weight: 100;
        padding: 0.5em;
    }

    .AE-logo {
        width: 1.5cm;
        margin: auto 0 1em 1em;
    }

    .leaf {
        margin-top: auto;      
        width: 1.5cm;  
    }

</style>
