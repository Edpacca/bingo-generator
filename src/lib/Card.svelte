<script lang="ts">
    export let id: number;
    export let size: number = 3;
    export let squares: number = 9;
    export let values: string[];
</script>

<div class="card-wrapper">
    <h2>card #{id}</h2>
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
        font-size: calc((3 / var(--grid-size)) * 1vw);
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        color: rgb(132, 101, 15);
        font-weight: 100;
        padding: 0.5em;
    }
</style>