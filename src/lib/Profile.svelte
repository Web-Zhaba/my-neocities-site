<script>
  import { onDestroy } from "svelte";

  const SQUINT_MS = 600;

  let squint = $state(false);
  let timer;

  function squintNow() {
    squint = true;
    clearTimeout(timer);
    timer = setTimeout(() => (squint = false), SQUINT_MS);
  }

  onDestroy(() => clearTimeout(timer));
</script>

<div class="flex flex-wrap items-center">
  <button type="button" onclick={squintNow} class="ml-5 cursor-pointer">
    <img
      src={squint ? "happy_closed_eyes.png" : "happy.png"}
      alt="MainPhoto"
      class="[image-rendering:pixelated] w-64 sm:w-80 backdrop-blur-[1px] bg-nothing-gray/40 border border-white/5 shadow-[inset_0_0_12px_rgba(255,255,255,0.03)] select-none"
    />
  </button>
  <div class="flex flex-col gap-2 ml-7 mb-1.5 mt-1.5">
    <h2 class="text-5xl sm:text-7xl select-none">Daniil<br /> Ponchick<br /></h2>
    <h3 class="text-2xl sm:text-3xl select-none">Software and Web Enthusiast</h3>
  </div>
</div>
