<script>
  import { onMount } from "svelte";

  let time = $state("");

  function updateTime() {
    const now = new Date();
    time = now.toLocaleTimeString("ru-RU", {
      hour: "2-digit",
      minute: "2-digit",
      second: "2-digit",
    });
  }

  onMount(() => {
    updateTime();
    const timer = setInterval(updateTime, 1000);
    return () => clearInterval(timer);
  });
</script>

<div class="flex items-baseline gap-3 ml-7 mb-1.5 mt-1.5">
  <span class="inline-block w-3 h-3 rounded-full bg-[#d71921] animate-pulse"></span>
  <span class="text-xl sm:text-2xl text-white/80">SYS.ONLINE: {time}</span>
</div>
