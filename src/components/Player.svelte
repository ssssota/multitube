<script lang="ts">
import { onMount, tick } from 'svelte';

  import youtube from 'youtube-player';
  export let id: string;

  $: playerId = `player-${id}`;
  $: tick().then(() => {
    const player = youtube(playerId, {
      videoId: id,
    });
    setTimeout(() => player.playVideo(), 500);
  });
</script>

<section>
  <div id={playerId}></div>
</section>

<style>
  section :global(iframe) {
    width: 100%;
  }
</style>
