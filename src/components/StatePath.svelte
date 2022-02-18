<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  import type { StateData, StateClickDetail } from './states-data';

  export let stateData: StateData;
  export let fill: string;

  const dispatcher = createEventDispatcher<{ stateclick: StateClickDetail }>();

  const handleClick = (e: MouseEvent): void => {
    dispatcher('stateclick', {
      clickX: e.clientX,
      clickY: e.clientY,
      ...stateData,
    });
  };
</script>

<path on:click={handleClick} class="state" d={stateData.svgPath} style="fill: {fill};" />

<style>
  .state {
    stroke: #000;
    stroke-width: 1;
  }

  .state:hover {
    fill-opacity: 0.5;
  }
</style>
