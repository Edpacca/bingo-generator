<script lang="ts">
  import Cards from './lib/Cards.svelte';
  import Setup from './lib/Setup.svelte'
  let numberOfCards: number;
  let cardSize: number; 
  let bingoValues: string = "";
  let uniqueBingoValues: string = "";
  let numberOfSquares = 9;
  let generated = false;
  let printView = false;

  const generate = () => {
    numberOfSquares = cardSize * cardSize;
    generated = bingoValues.length > 0 ? !generated: false;
  }

  const parseValues = () => {
    if (bingoValues) {
      
      let parsedBingoValues = bingoValues.split('\n');
      console.log(parsedBingoValues);
      let cardValues = [];

      for (let i = 0; i < cardSize * cardSize; i++) {
        cardValues.push(getRandomUniqueValue(parsedBingoValues, cardValues));
      }

      if (uniqueBingoValues) {
        let parsedUniqueBingoValues = uniqueBingoValues.split('\n');
        let uniqueIndex = getRandomIndex(cardSize * cardSize);
        cardValues[uniqueIndex] = parsedUniqueBingoValues[getRandomIndex(parsedUniqueBingoValues.length)];
      }
      
      console.log(cardValues);
      return cardValues;
    }
  }

  const getRandomUniqueValue = (sourceArray, targetArray) => {
    let index = Math.floor(Math.random() * sourceArray.length);
    let value = sourceArray[index];
    if (targetArray.includes(value)) {
      return getRandomUniqueValue(sourceArray, targetArray);
    }
    return value;
  }

  const getRandomIndex = (max) => {
    return Math.floor(Math.random() * max)
  }
</script>

<main>
  {#if generated}
    <button on:click={() => printView = !printView} class="print-view">🖶</button>
  {/if}
  {#if !printView}
    <h1>Bingo Generator</h1>
    <Setup 
      bind:cardSize={cardSize}
      bind:numberOfCards={numberOfCards}
      bind:bingoValues={bingoValues}
      bind:uniqueBingoValues={uniqueBingoValues}
      on:generate={generate}/>
  {/if}

  {#if generated}
    <Cards bind:cardSize={cardSize} bind:numberOfCards={numberOfCards} bind:numberOfSquares={numberOfSquares} parseValues={parseValues}/>
  {/if}
</main>

<style>

  .print-view {
    position: absolute;
    left: 0;
    top: 0;
    margin: 0;  
    padding: 0;
    background-color: transparent;
    border: 0;
    font-size: 2em;
    color: rgb(132, 101, 15);
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

</style>
