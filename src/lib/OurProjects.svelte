<script>
    import ProjectCarousel from "./ProjectCarousel.svelte";
</script>



<main>
    <h2>Our Projects</h2>
    <ProjectCarousel />
</main>



<style>
    main {
        width: 100%;
        background-color: var(--white);

        display: flex;
        flex-direction: column;
        align-items: center;

        box-shadow: 0 .5rem 0 1rem var(--white);
    }

    main h2 {
        margin: 1rem;
        color: var(--v1);
        font-weight: 900;
        font-size: 2rem;
        letter-spacing: .1rem;
    }
</style>