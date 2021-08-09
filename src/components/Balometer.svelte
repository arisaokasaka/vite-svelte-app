<script lang="ts">
  export let title: string;
  export let number: number;
  export let percentage: number;
</script>

<div class="balometer-container">
  <div>
    <p class="title">{title}</p>
    <p class="number">{number}</p>
  </div>
  <div>
    <span class="percentage">{percentage}</span>
  </div>
</div>

<style>
  p {
    margin: 0;
  }

  .balometer-container {
    display: flex;
    justify-content: space-between;
    width: 100%;
    background-color: teal;
    color: white;
    border-radius: 8px;
    padding: 32px 16px;
  }

  .title {
    color: darkgrey;
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
