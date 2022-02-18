<script lang="ts">
  import { statesData } from './states-data';
  import StatePath from './StatePath.svelte';
</script>

<svg width="960" height="600">
  {#each statesData as stateData (stateData.id)}
    <StatePath on:stateclick {stateData} fill="hsl(350, 84%, 42%)" />
  {/each}
</svg>
