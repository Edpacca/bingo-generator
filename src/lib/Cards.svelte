<script>
    import Card from "./Card.svelte";
    export let numberOfCards;
    export let numberOfSquares;
    export let cardSize;
    export let parseValues;
</script>

<div class="cards">
    {#each Array(numberOfCards) as card, i}
      <Card id={i + 1} size={cardSize} squares={numberOfSquares} values={parseValues()}/>
    {/each}
</div>

<style>
    .cards {
        display: grid;
        grid-template-columns: 1fr 1fr;
        row-gap: 6.5cm;
    }
</style>
