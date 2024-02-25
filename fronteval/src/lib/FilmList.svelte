<!-- FilmList.svelte -->
<script>
    export let films;
  </script>
    
  <div>
    <h2>Films</h2>
    {#if films.length > 0}
      {#each films as film}
        <div>{film.title} - {film.genre}</div>
      {/each}
    {:else}
      <p>Aucun film trouvé.</p>
    {/if}
  </div>
  