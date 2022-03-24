<script>
  export let progress_width = 0;
</script>

<div bp="grid">
  <div bp="offset-5@md 4@md 12@sm" class="progress-container">
    <div class="progress-bar" style="width: {progress_width}%" />
  </div>
</div>

<style>
  .progress-container {
    margin: 20px 0;
    border: solid 1px darkgrey;
  }
  .progress-bar {
    height: 30px;
    background-color: rgb(56, 199, 199);
  }
</style>
