<script lang="ts">
  import Balometer from "./components/Balometer.svelte";
  import Chart from "./components/Chart.svelte";
</script>

<main>
  <div>
    <h1>Dashboard</h1>
    <section class="balometers">
      <Balometer title="title" percentage={32} number={1} />
      <Balometer title="title" percentage={32} number={1} />
      <Balometer title="title" percentage={32} number={1} />
    </section>
    <section class="chart-area">
      <Chart />
    </section>
  </div>
</main>

<style>
  :global(html) {
    background-color: #7f5f00;
  }

  :global(body) {
    margin: 0;
    padding: 0;
  }

  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  main {
    width: fit-content;
    padding: 12px 36px;
    margin: 0 auto;
  }

  h1 {
    color: white;
  }
  .balometers {
    display: flex;
    gap: 12px;
  }

  .chart-area {
    margin-top: 12px;
  }
</style>
