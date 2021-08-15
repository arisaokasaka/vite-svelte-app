<script lang="ts">
  import { onMount } from "svelte";

  let promise = getChartData();
  async function getChartData() {
    const res = await fetch("/api/chart_data.json");
    const data = await res.json();
    if (res.ok) {
      return data.chart;
    } else {
      throw new Error();
    }
  }

  onMount(() => {
    const canvas = document.getElementById("chart-canvas") as HTMLCanvasElement;
    const ctx = canvas.getContext("2d");

    // 横線
    ctx.fillStyle = "rgba(255, 255, 255, 0.466)";
    ctx.strokeStyle = "rgba(255, 255, 255, 0.466)";
    ctx.lineWidth = 1;
    for (let index = 0; index <= 10; index++) {
      switch (index) {
        case 0:
          ctx.fillText(`   ${index}%`, 0, -36 * index + 400);
          break;
        case 10:
          ctx.fillText(`${index}0%`, 0, -36 * index + 400);
          break;
        default:
          ctx.fillText(` ${index}0%`, 0, -36 * index + 400);
      }
      ctx.beginPath();
      ctx.moveTo(40, -36 * index + 396);
      ctx.lineTo(652, -36 * index + 396);
      ctx.closePath();
      ctx.stroke();
    }

    monthIndex();
    async function monthIndex() {
      await promise.then((res) => {
        res.map((el, index) => {
          ctx.save();
          ctx.fillStyle = "rgba(255, 255, 255, 0.466)";
          ctx.translate(-90, index * 13.4);
          ctx.rotate(-0.08 * Math.PI);
          ctx.fillText(`${el.month}`, index * 54 + 24, 440);
          ctx.restore();

          const ratio = el.core_target / el.total;
          ctx.beginPath();
          ctx.arc(index * 54 + 52, 420 - ratio * 360 - 22, 3, 0, 2 * Math.PI);
          ctx.lineWidth = 0;
          ctx.strokeStyle = "orange";
          ctx.fillStyle = "orange";
          ctx.fill();
          ctx.stroke();
        });
      });
    }
  });
</script>

<div class="chart-container">
  <canvas id="chart-canvas" width="672" height="420">chart</canvas>
</div>

<style>
  .chart-container {
    width: fit-content;
    padding: 24px;
    background-color: #004c4c;
    border-radius: 8px;
  }
</style>
