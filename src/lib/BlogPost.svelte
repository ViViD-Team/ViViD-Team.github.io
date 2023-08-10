<script>
    export let data;
</script>



<main>
    <a href="#top">
        <div class="image"></div>
        <div class="titleContainer">
            <p>Blog Post Summary Blog Post Summary Blog Post Summary Blog Post Summary</p>
        </div>
    </a>
</main>



<style>
    main {
        margin: 1rem;
        
        height: 14rem;
        aspect-ratio: 1 / 1;

        background-color: var(--white-transparent);
        border-radius: 1rem;

        overflow: hidden;
    }

    main a {
        width: 100%;
        height: 100%;

        display: flex;
        flex-direction: column;

        text-decoration: none;
    }

    .image {
        width: 100%;
        flex: 2;

        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;

        background-color: var(--white-transparent-2);
    }

    .titleContainer {
        width: 100%;
        flex: 1;

        display: grid;
        place-items: center;

        overflow: hidden;
    }

    .titleContainer p {
        color: var(--white);
        font-weight: 500;
        font-size: .8rem;
        
        max-width: calc(100% - 1rem);
        text-align: center;
    }
</style>