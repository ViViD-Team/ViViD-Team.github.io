<script>
  import Landing from "./lib/Landing.svelte";
  import OurProjects from "./lib/OurProjects.svelte";
  import BlogOverview from "./lib/BlogOverview.svelte";
  import Footer from "./lib/Footer.svelte";
  import Blog from "./lib/Blog.svelte";
</script>



<main>
  {#if new URL(String(window.location)).searchParams.get("blog")}
    <Blog />
  {:else}
    <Landing />
    <OurProjects />
    <BlogOverview />
    <Footer />
  {/if}
</main>



<style>
  main {
    overflow: hidden;
  }
</style>