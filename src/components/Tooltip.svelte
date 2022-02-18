<script lang="ts">
  export let stateName: string;
  export let chapterName: string;
  export let chapterUrl: string;
  export let clickX: number;
  export let clickY: number;
  export let hidden = true;

  let left: string;
  let top: string;

  $: left = clickX.toString() + 'px';
  $: top = clickY.toString() + 'px';
</script>

<div class="tooltip" style="left: {left}; top: {top};" {hidden}>
  <h4>{stateName}</h4>
  <table>
    <tr>
      <td>Chapter Name:</td><td>{chapterName}</td>
    </tr>
    <tr>
      <td>Chapter Site:</td><td><a href={chapterUrl}>{chapterUrl}</a></td>
    </tr>
  </table>
</div>

<style>
  .tooltip {
    position: absolute;
    text-align: center;
    padding: 20px;
    margin: 10px;
    font: 12px sans-serif;
    background: hsl(0, 50%, 10%);
    border: 1px;
    border-radius: 2px;
    pointer-events: none;
    color: white;
  }

  .tooltip h4 {
    margin: 0;
    font-size: 14px;
  }

  .tooltip table {
    table-layout: fixed;
  }

  .tooltip tr td {
    padding: 0;
    margin: 0;
    color: white;
  }

  .tooltip tr td:nth-child(1) {
    width: 100px;
  }

  .tooltip tr td:nth-child(2) {
    text-align: center;
    pointer-events: auto;
  }
</style>
