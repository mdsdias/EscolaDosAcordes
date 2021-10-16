<script>
  export let selected;
</script>

{#each selected as s}
  <img src={s.src} alt={s.name} />
  <div>
    <h2>{s.name}</h2>
    {#if typeof s.artists === "object"}
      {#each s.artists as k}
        <h4>{k}</h4>
      {/each}
    {:else}
      <h4>{s.artists}</h4>
    {/if}
  </div>
{/each}
