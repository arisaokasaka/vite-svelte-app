<script lang="ts">
  import { onMount } from "svelte";
  export let title: string;
  export let number: number;
  export let percentage: number;
  export let canvas_id: string;
  export let barometer_color: string;

  onMount(() => {
    const canvas = document.getElementById(canvas_id) as HTMLCanvasElement;
    const ctx = canvas.getContext("2d");

    ctx.beginPath();
    ctx.strokeStyle = "grey";
    ctx.lineWidth = 5;
    ctx.arc(54, 54, 51.5, 0, 2 * Math.PI);
    ctx.stroke();

    ctx.beginPath();
    ctx.strokeStyle = barometer_color;
    ctx.lineWidth = 5;
    ctx.arc(
      54,
      54,
      51.5,
      -0.5 * Math.PI,
      (percentage / 100) * (2 * Math.PI) - 0.5 * Math.PI
    );
    ctx.stroke();
  });
</script>

<div class="barometer-container">
  <div>
    <p class="title">{title}</p>
    <p class="number">{number}</p>
  </div>
  <div class="graph-container">
    <canvas id={canvas_id} width="108" height="108">
      {title}: {percentage}%
    </canvas>
    <span class="percentage">{percentage}<span>%</span></span>
  </div>
</div>

<style>
  .graph-container {
    position: relative;
    width: fit-content;
    height: fit-content;
  }

  span {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 0 0 4px 2px;
  }

  span > span {
    position: initial;
    font-size: 12px;
  }

  p {
    margin: 0;
  }

  .barometer-container {
    display: flex;
    justify-content: space-between;
    width: 100%;
    background-color: #004c4c;
    color: white;
    border-radius: 8px;
    padding: 32px 16px;
  }

  .title {
    color: darkgrey;
    font-size: 0.8rem;
  }

  .number {
    margin-top: 8px;
    font-size: 24px;
    font-weight: 600;
  }

  .percentage {
    font-size: 20px;
  }
</style>
