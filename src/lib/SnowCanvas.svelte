<script>
  import { onMount } from "svelte";

  let snowCanvas;

  onMount(() => {
    const canvas = snowCanvas;
    if (!canvas.getContext) return;
    if (window.matchMedia("(prefers-reduced-motion: reduce)").matches) return;

    const ctx = canvas.getContext("2d");
    const dpr = Math.min(window.devicePixelRatio || 1, 2);
    let w = 0;
    let h = 0;
    let flakes = [];
    let raf;

    const resize = () => {
      w = window.innerWidth;
      h = window.innerHeight;
      canvas.width = Math.floor(w * dpr);
      canvas.height = Math.floor(h * dpr);
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    };

    const spawn = (initial) => ({
      x: Math.random() * w,
      y: initial ? Math.random() * h : -4,
      r: Math.random() < 0.8 ? 1 : 2,
      v: 0.25 + Math.random() * 0.6,
      drift: Math.random() * Math.PI * 2,
    });

    const step = () => {
      ctx.clearRect(0, 0, w, h);
      ctx.fillStyle = "rgba(219, 224, 235, 0.55)";
      for (const f of flakes) {
        f.y += f.v;
        f.drift += 0.01;
        f.x += Math.sin(f.drift) * 0.3;
        if (f.y > h + 4) Object.assign(f, spawn(false));
        ctx.fillRect(Math.round(f.x), Math.round(f.y), f.r, f.r);
      }
      raf = requestAnimationFrame(step);
    };

    resize();
    flakes = Array.from({ length: 90 }, () => spawn(true));
    window.addEventListener("resize", resize);
    raf = requestAnimationFrame(step);

    return () => {
      cancelAnimationFrame(raf);
      window.removeEventListener("resize", resize);
    };
  });
</script>

<canvas bind:this={snowCanvas} id="snow" aria-hidden="true"></canvas>
