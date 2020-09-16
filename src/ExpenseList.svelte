<script>
  import SectionTitle from "./Title.svelte";
  export let expenses = [];
  import Expense from "./Expense.svelte";
  export let clearExpenses;
</script>

<section>
  <SectionTitle title="expense list" />
  <ul>
    {#each expenses as expense}
      <Expense {...expense} />
    {:else}
      <h2>No Expenses Added To The List</h2>
    {/each}
  </ul>
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={() => clearExpenses()}>
    Clear expenses
  </button>
</section>
