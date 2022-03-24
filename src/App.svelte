<script>
  import Timer from "./Timer.svelte";
  import HowTo from "./HowTo.svelte";

  let audio;

  function timerend(e) {
    audio.play();
  }
</script>

<h1>HandWashing app</h1>

<Timer on:end={timerend} />
<HowTo />

<audio bind:this={audio}>
  <source src="sound.wav" />
</audio>

<style>
  h1 {
    text-align: center;
  }
</style>
