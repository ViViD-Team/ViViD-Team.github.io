<script>
    export let data;
</script>



<main>
    <a href="/?blog={data.id}">
        <div class="imageContainer">
            <div class="image" style="background-image: url({data.imageResource});"></div>
        </div>
        <div class="titleContainer">
            <p>{data.title}</p>
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

        transition: transform .5s cubic-bezier(0, 0, 0, .9);
    }

    main:is(:hover, :focus) {
        transform: translateY(-.1rem);
    }

    main:is(:hover, :focus) .image {
        transform: scale(1.1);
    }

    main a {
        width: 100%;
        height: 100%;

        display: flex;
        flex-direction: column;

        text-decoration: none;
    }

    .imageContainer {
        width: 100%;
        flex: 2;

        overflow: hidden;
    }

    .image {
        width: 100%;
        height: 100%;
        
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;

        background-color: var(--white-transparent-2);
        transition: transform .5s cubic-bezier(0, 0, 0, .9);
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