<script>
  import { setContext } from "svelte";
  //components
  import Navbar from "./Navbar.svelte";
  import ExpenseList from "./ExpenseList.svelte";
  import expensesData from "./expenses";
  import Totals from "./Totals.svelte";
  //variables
  let expenses = [...expensesData];
  //reactivity
  let total = 0;
  $: total = expenses.reduce((acc, curr) => {
    return (acc += curr.amount);
  }, 0);
  function removeExpense(id) {
    expenses = expenses.filter((item) => item.id !== id);
  }
  function clearExpenses() {
    expenses = [];
  }
  setContext("remove", removeExpense);
</script>

<Navbar />
<main class="content">
  <Totals title="Total Expenses" {total} />
  <ExpenseList {expenses} {clearExpenses} />
</main>
