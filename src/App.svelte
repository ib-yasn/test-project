<script>
  import Component1 from './Component1.svelte';
  import Component2 from './Component2.svelte';
  import Component3 from './Component3.svelte';

  export let name;

  let tableConfig = {
    columnDef: [
      {
        title: 'Name',
        prop: 'name',
      },
      {
        title: 'Protocol',
        prop: 'prototcol',
      },
      {
        title: 'Port',
        prop: 'port',
      },
      {
        title: 'Rule',
        prop: 'rule',
      },
      {
        title: 'Attached Groups',
        prop: 'attachedGroups',
      },
      {
        title: 'Status',
        prop: 'status',
      },
    ],
    globalActions: [{ name: 'Create New', id: 'add' }],
    rowActions: [
      { name: 'Delete', id: 'delete' },
      { name: 'Edit', id: 'edit' },
    ],
  };

  let tableData = [
    {
      name: 'Load Balancer 1',
      prototcol: 'HTTP',
      port: '8080',
      rule: 'Round Robin',
      attachedGroups: 'VGroup 1',
      status: 'Active',
    },
    {
      name: 'Load Balancer 2',
      prototcol: 'HTTP',
      port: '8080',
      rule: 'Least Connections',
      attachedGroups: 'VGroup 1',
      status: 'Disabled',
    },
    {
      name: 'Load Balancer 3',
      prototcol: 'HTTP',
      port: '8088',
      rule: 'Round Robin',
      attachedGroups: 'VGroup 2',
      status: 'Starting',
    },
  ];
  function handleAction(event) {
    const actionDetails = event.detail;
    switch (actionDetails.id) {
      case 'add':
        alert('Create action');
        break;
      case 'delete':
        alert('Delte action For ' + actionDetails.data.name);
        break;
      case 'edit':
        alert('Edit action For ' + actionDetails.data.name);
        break;
    }
  }
</script>

<main>
  <h1>Hello {name}!</h1>

  <Component1 />
  <Component2 />
  <Component3 {tableConfig} {tableData} on:action={handleAction} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
