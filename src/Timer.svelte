<script>
  import { createEventDispatcher } from "svelte";
  import Progress from "./Progress.svelte";

  const totalsecond = 20;
  let secondsleft = totalsecond;
  let isRunning = false;
  $: progress_bar_width = ((totalsecond - secondsleft) / totalsecond) * 100;

  const dispatch = createEventDispatcher();

  function countdown() {
    isRunning = true;
    const timer = setInterval(() => {
      secondsleft -= 1;
      if (secondsleft == -1) {
        clearInterval(timer);
        isRunning = false;
        secondsleft = totalsecond;
        dispatch("end");
      }
    }, 1000);
  }
</script>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondsleft}</h2>
</div>
<Progress progress_width={progress_bar_width} />
<div bp="grid">
  <button
    disabled={isRunning}
    bp="offset-5@md 4@md 12@sm"
    class="start"
    on:click={countdown}
  >
    Start
  </button>
</div>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: royalblue;
    width: 100%;
    margin: 10px 0;
  }
  .start[disabled] {
    background-color: grey;
    cursor: not-allowed;
  }
</style>
