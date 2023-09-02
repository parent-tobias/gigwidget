<script>
  import { afterUpdate, beforeUpdate, onMount } from "svelte";

  // given an instrument and a chord, we should be able to generate a chord chart dynamically.
  import { keys, instruments, chordOnInstrument, chordToNotes } from "../../services/musicUtils";
  import { SVGuitarChord } from "svguitar";
  export let instrument;
  export let chord;

  let container;

  const showChord =()=>{
    const instrumentObject = instruments.find(({name})=>name===instrument)

    const chordFinder = chordOnInstrument(
      instrumentObject
    );

    // given the chord name (G7, Bbmin), we need the notes in the chord
    const chordObject = chordToNotes(chord);

    const strings = chordFinder(chordObject);

    let maxFrets = Math.max(...strings.map(([,fret])=>fret) );
    maxFrets = maxFrets >=4 ? maxFrets : 4;

    let divEl = document.createElement("div");

    const chart = new SVGuitarChord(divEl);
    chart
      .configure({
        strings: instrumentObject?.strings.length,
        frets: maxFrets,
        position: 1,
        tuning: [...instrumentObject?.strings]
      })
      .chord({
        barres: [], 
        fingers: strings, 
      })
      .draw();

      container.appendChild(divEl.firstChild);
  } 


  beforeUpdate(()=>{
    if(container){
      while(container.firstChild) container.firstChild.remove();
      showChord();
    }
  })

</script>
<div class='chord chart'>
  <span>{chord}</span>
  <div bind:this={container} />  
</div>

<style>
  .chord span {
    font-weight: 800;
  }
  .chord {
    width: 10%;
    padding: .25em;
  }
</style>