<script lang="ts">
  export let onAdd: (id: string) => void;
  let id = '';

  const onsubmit: svelte.JSX.EventHandler<Event, HTMLFormElement> = (e) => {
    e.preventDefault();
    onAdd(id);
    id = '';
  }
</script>

<form on:submit={onsubmit}>
  <input type="text" bind:value={id} placeholder="Youtube Video ID">
  <button type="submit">ADD</button>
</form>

<style>
  form {
    position: fixed;
    bottom: 0;
    right: 0;
    background-color: #f5f5f5;
    padding: 2px;
  }
</style>
