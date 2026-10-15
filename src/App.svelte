<script>
  import Clock from "./lib/Clock.svelte";
  import SnowCanvas from "./lib/SnowCanvas.svelte";
  import Profile from "./lib/Profile.svelte";
  import LinkList from "./lib/LinkList.svelte";
  import { projects } from "./lib/links.js";
  import AboutMe from "./lib/AboutMe.svelte";
</script>

<section
  class="min-h-screen bg-nothing-black text-nothing-white selection:bg-nothing-red selection:text-white relative overflow-x-hidden"
>
  <SnowCanvas />
  <div class="scan" aria-hidden="true"></div>
  <header></header>

  <main>
    <Clock />
    <Profile />
    <LinkList title="My projects:" items={projects} />
    <AboutMe />
    <!-- <LinkList
      title="My socials:"
      items={[{ name: "Telegram", href: "#", icon: "telegramFav.png" }]}
    /> -->
  </main>

  <footer></footer>
</section>
