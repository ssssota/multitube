<script lang="ts">
import { onMount } from 'svelte';
import Adder from './components/Adder.svelte';
import YoutubePlayer from './components/Player.svelte';
let idList: string[] = [];
let columns: number = 3;

onMount(() => {
  const url = new URL(location.href);
  idList = url.searchParams.getAll('id');
  columns = Number(url.searchParams.get('cols')) || columns;
});

const onAdd = (id: string) => {
  idList = [...idList, id];
  const newLocation = new URL(location.href);
  newLocation.searchParams.append('id', id);
  history.replaceState(null, 'Multitube', newLocation.href);
}
</script>

<main style={`grid-template-columns:${' 1fr'.repeat(columns)};`}>
  {#each idList as id}
    <YoutubePlayer {id} />
  {/each}
  <Adder {onAdd} />
</main>

<style>
  main {
    display: grid;
  }
</style>
