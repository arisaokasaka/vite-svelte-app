<script lang="ts">
  import Barometer from "./components/Barometer.svelte";
  import Chart from "./components/Chart.svelte";

  let promise = getBarometerData();
  async function getBarometerData() {
    const res = await fetch("/api/barometer_data.json");
    const data = await res.json();
    if (res.ok) {
      return data.barometer;
    } else {
      throw new Error();
    }
  }
</script>

<main>
  <div>
    <h1>Dashboard</h1>
    <section class="barometers">
      {#await promise}
        <p>loading...</p>
      {:then res}
        <Barometer
          barometer_color="chocolate"
          canvas_id="canvas_3"
          title="TWENTIES"
          percentage={res.twenties.percentage}
          number={res.twenties.number}
        />
        <Barometer
          barometer_color="orange"
          canvas_id="canvas_2"
          title="PASSED"
          percentage={res.passed.percentage}
          number={res.passed.number}
        />
        <Barometer
          barometer_color="gold"
          canvas_id="canvas_1"
          title="AGREEMENT"
          percentage={res.agreement.percentage}
          number={res.agreement.number}
        />
      {/await}
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
