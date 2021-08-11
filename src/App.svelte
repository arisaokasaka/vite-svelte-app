<script lang="ts">
  import Barometer from "./components/Barometer.svelte";
  import Chart from "./components/Chart.svelte";
</script>

<main>
  <div>
    <h1>Dashboard</h1>
    <section class="barometers">
      <Barometer
        barometer_color="chocolate"
        canvas_id="canvas_3"
        title="title"
        percentage={32}
        number={1}
      />
      <Barometer
        barometer_color="orange"
        canvas_id="canvas_2"
        title="title"
        percentage={50}
        number={1}
      />
      <Barometer
        barometer_color="gold"
        canvas_id="canvas_1"
        title="title"
        percentage={32}
        number={1}
      />
    </section>
    <section class="chart-area">
      <Chart />
    </section>
  </div>
</main>

<style>
  :global(html) {
    background-color: #008080;
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
  .barometers {
    display: flex;
    gap: 12px;
  }

  .chart-area {
    margin-top: 12px;
  }
</style>
