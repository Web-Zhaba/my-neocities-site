<script>
  let { title, items } = $props();
</script>

<div class="flex flex-col ml-7 mb-1.5 mt-5">
  <span class="text-2xl sm:text-3xl text-white/80">{title}</span>
  <ul class="flex-col gap-2 font-space max-w-fit">
    {#each items as item (item.name)}
      <li
        class="p-2 mt-2 mb-2 rounded-4xl backdrop-blur-[1px] bg-nothing-gray/40 border border-white/5 shadow-[inset_0_0_12px_rgba(255,255,255,0.03)] select-none"
      >
        <a class="flex gap-3 items-center" href={item.href} aria-label={item.name}>
          <img
            src={item.icon}
            alt={item.name}
            class="[image-rendering:pixelated] w-12 h-12"
          />
          <h3 class="text-3xl sm:text-4xl">{item.name}</h3>
        </a>
      </li>
    {/each}
  </ul>
</div>
