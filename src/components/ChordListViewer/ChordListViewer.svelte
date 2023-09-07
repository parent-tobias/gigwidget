<script>
  import Chord from "../../lib/Chord/Chord.svelte";

  export let chords = [];
  
  export let instrument;

  let displayedChords = [...new Set(chords)];
  console.log(chords, displayedChords);
  
</script>

<div class='chords-list-panel'>
  {#each displayedChords as chord}
  <Chord {chord} {instrument} />
  {/each}
</div>

<style>
  .chords-list-panel {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
    justify-content: space-between;
  }
  .chords-list-panel :global(.chord) {
    width: 6vw;
    height: 4vh;
  }
</style>