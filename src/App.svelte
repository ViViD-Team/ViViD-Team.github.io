<script>
  import Landing from "./lib/Landing.svelte";
  import OurProjects from "./lib/OurProjects.svelte";
  import BlogOverview from "./lib/BlogOverview.svelte";
  import Footer from "./lib/Footer.svelte";
    import { onMount } from "svelte";

  onMount(() => {
    fetch("_blog/testEntry.json").then(data => {
      console.log(data);
    });
  });
</script>



<main>
  <Landing />
  <OurProjects />
  <BlogOverview />
  <Footer />
</main>



<style>
  main {
    overflow: hidden;
  }
</style>