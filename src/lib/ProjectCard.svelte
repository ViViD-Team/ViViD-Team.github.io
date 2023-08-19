<script>
    export let data;
</script>



<main>
    <div class="window">
        <div class="image" style="background-image: url({data.image_resource});"></div>
        <div class="titleContainer"><h3>{data.name}</h3></div>
        <div class="descriptionContainer"><p>{data.description}</p></div>
    </div>

    <div class="actionStrip">
        {#if data.findoutmore_href}
        <a href="{data.findoutmore_href}" class="solid">Find Out More</a>
        {/if}
        {#if data.download_href}
        <a href="{data.download_href}" class="light">Download</a>
        {/if}
    </div>
</main>



<style>
    main {
        height: calc(100% - 4rem);
        aspect-ratio: 16 / 9;

        border-radius: 1rem;

        display: flex;
        flex-direction: column;

        overflow: hidden;
    }

    .window {
        position: relative;

        width: 100%;
        height: calc(100% - 4rem);

        display: flex;

        overflow: hidden;
    }

    .image {
        position: absolute;

        width: 100%;
        height: 100%;

        top: 0;
        left: 0;

        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;


        background-color: white;
    }

    :is(.titleContainer, .descriptionContainer) {
        height: 100%;
        flex: 1;
    }

    :is(.titleContainer, .descriptionContainer) :is(h3, p) {
        color: var(--black);
    }

    .titleContainer {
        background: linear-gradient(to right, var(--black-transparent-05), transparent);
    }

    .titleContainer h3 {
        position: absolute;
        top: 1rem;
        left: 1em;

        font-size: 1.5rem;
    }

    .descriptionContainer {
        display: flex;
        align-items: center;
        justify-content: flex-end;

        background: linear-gradient(to left, var(--black-transparent-05), transparent);
    }

    .descriptionContainer p {
        margin-right: 1rem;
        max-height: calc(100% - 2rem);
        width: 55%;

        text-align: end;

        font-weight: 400;
        font-size: .9rem;
        letter-spacing: -.05em;
    }


    .actionStrip {
        width: 100%;
        flex: 1;

        padding-left: 1rem;

        display: flex;
        align-items: center;

        background-color: var(--v1);

        gap: 1rem;
    }

    .actionStrip a {
        height: calc(100% - 2rem);
        padding-left: 1.5rem;
        padding-right: 1.5rem;

        border-radius: .8rem;

        display: grid;
        place-items: center;

        flex-shrink: 0;

        font-size: .8rem;
        font-weight: 600;

        text-decoration: none;

        transition: transform .5s cubic-bezier(0, 0, 0, .9);
    }

    .actionStrip a:is(:hover, :focus) {
        transform: translateY(-.1rem);
    }

    .actionStrip a.solid {
        background-color: var(--white);
        color: var(--v1);
    }

    .actionStrip a.light {
        box-shadow: inset 0 0 0 .1rem var(--white);
        color: var(--white);
    }

    @media only screen and (max-width: 100vh) {
        main {
            aspect-ratio: 9 / 16;
            background-color: var(--v1);
        }

        .image {
            margin-top: 4rem;
            height: calc(100% - 12rem);
        }

        :is(.titleContainer, .descriptionContainer) {
            background: none;
        }

        .descriptionContainer {
            position: absolute;
            flex: unset;

            width: 100%;
            height: 8rem;

            left: 0;
            bottom: 0;

            display: grid;
            place-items: center;
        }

        .descriptionContainer p {
            margin: 0;

            max-height: unset;

            width: calc(100% - 1rem);
            height: 7rem;

            text-align: justify;
            font-size: .8rem;
            color: var(--white);
        }

        .titleContainer h3 {
            color: var(--white);
        }

        .actionStrip {
            padding: 0;
            gap: unset;
            justify-content: space-evenly;
        }
    }

</style>