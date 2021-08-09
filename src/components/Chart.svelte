<div class="chart-container">
  <!-- <table border="1"> -->
  <table>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
    <tr><td /></tr>
  </table>
</div>

<style>
  .chart-container {
    width: fit-content;
    padding: 12px 24px 36px 36px;
    background-color: teal;
    border-radius: 8px;
  }

  table {
    width: 640px;
    margin: 12px 24px;
    border-collapse: collapse;
  }

  tr {
    position: relative;
    height: 28px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.466);
  }

  tr:first-child::before,
  tr:nth-child(2)::before,
  tr:nth-child(3)::before,
  tr:nth-child(4)::before,
  tr:nth-child(5)::before,
  tr:nth-child(6)::before,
  tr:nth-child(7)::before,
  tr:nth-child(8)::before,
  tr:nth-child(9)::before,
  tr:nth-child(10)::before,
  tr:nth-child(11)::before {
    content: "100%";
    position: absolute;
    top: 21px;
    right: calc(100%);
    color: white;
    font-size: 8px;
    padding-right: 4px;
  }

  tr:nth-child(2)::before {
    content: "90%";
  }
  tr:nth-child(3)::before {
    content: "80%";
  }
  tr:nth-child(4)::before {
    content: "70%";
  }
  tr:nth-child(5)::before {
    content: "60%";
  }
  tr:nth-child(6)::before {
    content: "50%";
  }
  tr:nth-child(7)::before {
    content: "40%";
  }
  tr:nth-child(8)::before {
    content: "30%";
  }
  tr:nth-child(9)::before {
    content: "20%";
  }
  tr:nth-child(10)::before {
    content: "10%";
  }
  tr:nth-child(11)::before {
    content: "0%";
  }
</style>
