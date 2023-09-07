<script>
  /****
   * This should take in the ChordSheetViewer and the ChordList components,
   * and render them both. I think.
   ****/
  import ChordSheetViewer from "../ChordSheetViewer/ChordSheetViewer.svelte";
  import ChordListViewer from "../ChordListViewer/ChordListViewer.svelte";

  const song = `{title: Let it be}
{subtitle: ChordSheetJS example version}
{key: C}
{capo: 5}
{composer: John Lennon}
{composer: Paul McCartney}
{chordsize: 12px}

{textcolour: maroon}
Written by: %{composer}
{textcolour}
Lyrics by: %{lyricist|%{}|(unknown)}

{chordcolour: purple}
{chordfont: monospace}
{chordsize: 150%}
{textcolour: navy}
{textfont: sans-serif}
{textsize: 120%}

{start_of_chorus}
[D7]Look for the [G]Bear Necessities,
the [C]simple bear necessities,
for[G]-get a[E7]-bout your
[A7]worries and your [D7-alt]strife;
I mean the [G]Bear Nec[G7]essities,
they're [C]why a bear can
 [C7]rest at ease, with
 [G]Just the [E7]Bear Neces[A7]-ities
 of [D7-alt]life!`;
</script>

<div class='song-container'>
  <ChordSheetViewer {song} mode='text'/>
  <ChordListViewer instrument='Standard Ukulele' chords={['A7','D','G','D','B7','E7','D7-alt','D','D7','G','G7','D','B7','E7','D7-alt']} />
</div>

<style>
  .song-container {
    display: grid;
    grid-template-columns: auto 25vw;
    grid-template-areas: header header
                         song chords
                         footer footer;
  }

  .song-container > .songsheet-panel {
    grid-area: song;
  }
  .song-container > .chords-list-panel{
    grid-area: chords;
  }
</style>