<script>
  import { createEventDispatcher } from 'svelte';
  // Please build a dynamic table component, based on the design provided plus an action column.
  export let tableConfig;
  export let tableData;

  const dispatch = createEventDispatcher();

  function generalActionHandler(id, data) {
    dispatch('action', {
      id: id, 
      data: data
    });
  }
</script>

<h1>Table</h1>
{#each tableConfig.globalActions as action}
  <button on:click={() => generalActionHandler(action.id)}> {action.name} </button>
{/each}
<table>
  <thead>
    <tr>
      {#each tableConfig.columnDef as col}
        <th>{col.title}</th>
      {/each}
      {#if tableConfig.rowActions && tableConfig.rowActions.length > 0}
        <th>Actions</th>
      {/if}
    </tr>
  </thead>
  <tbody>
    {#each tableData as row}
      <tr>
        {#each tableConfig.columnDef as col}
          <td>{row[col.prop]}</td>
        {/each}
        {#if tableConfig.rowActions && tableConfig.rowActions.length > 0}
            <td>
              {#each tableConfig.rowActions as action}
                <button  on:click={() => generalActionHandler(action.id, row)}> {action.name} </button>
              {/each}
            </td>
          {/if}
      </tr>
    {/each}
  </tbody>
</table>
