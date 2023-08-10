<script>
    import ViViD from "../assets/ViViD.svg";
    import BlobBackground from "../assets/blobBackground.svg"; 

    import { onMount } from "svelte";

    let postJSON;
    onMount(function() {
        // Fetch Post
        let postID = new URL(window.location).searchParams.get("blog");

        fetch(`/blog/${postID}.json`).then(res => res.json().then(data => {
            postJSON = data;
        }));
    });
</script>



<main>
    <div class="patternBackground" style="background-image: url({BlobBackground});"></div>
    <div class="logoContainer">
        <a href="/"><img src={ViViD} alt=""></a>
    </div>
    {#if postJSON}
        <div class="headerContainer">
            <div class="outer dash"></div>
                <h2>{postJSON.author}</h2>
            <div class="dash"></div>
                <h1>{postJSON.title}</h1>
            <div class="dash"></div>
                <h2>{postJSON.date}</h2>
            <div class="outer dash"></div>
        </div>

        <div class="content">
            {#each postJSON.body as item}

                {#if typeof(item) == "object"}

                    {#if item.type == "img"}
                        <img src="{item.src}" alt="">
                    {/if}

                    {#if item.type == "buttons"}
                        <div class="buttonsLayout">
                            {#each item.buttons as button}
                                <a tabindex="0" href={button.href} class="button {button.solid ? "solid" : "weak"}" style="
                                    --ownColor: {button.color || "var(--white)"};
                                ">
                                    <h4>{button.text}</h4>
                                </a>
                            {/each}
                        </div>
                    {/if}

                    {#if item.type == "composite"}
                        <p>
                            {#each item.spans as span}
                                {#if span.href}
                                    <a href="{span.href}">
                                        <span style="{span.style}">
                                            {span.text}
                                        </span>
                                    </a>
                                {:else}
                                    <span style="{span.style}">
                                        {span.text}
                                    </span>
                                {/if}
                            {/each}
                        </p>
                    {/if}

                {:else}

                    <p>{item}</p>
                {/if}

            {/each}
        </div>
    {/if}
</main>



<style>
    main {
        position: relative;

        width: 100vw;
        min-height: 100vh;

        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .patternBackground {
        position: absolute;

        top: 0;
        left: 0;

        width: 100%;
        height: 100%;

        background-size: contain;
        filter: blur(20vh);
    }


    .logoContainer {
        width: 100%;
        height: 4rem;

        display: flex;
        align-items: center;
    }

    .logoContainer :is(img, a) {
        height: 2rem;
        margin-left: 1rem;
    }

    .logoContainer a>img {
        height: 100%;
    }

    .headerContainer {
        width: 100%;
        min-height: 4rem;

        display: flex;
        align-items: center;
        justify-content: space-evenly;

    }

    h1 {
        font-size: 2rem;
        font-weight: 900;
    }

    h2 {
        font-size: 1rem;
        font-weight: 500;
    }

    .dash {
        margin: 1rem;

        height: .1rem;
        flex: 1;

        border-radius: .05rem;
        background-color: var(--white);
    }

    .dash.outer {
        flex: unset;
        width: 4rem;
    }


    .content {
        margin-top: 4rem;
        margin-bottom: 12rem;

        width: calc(100% - 8rem);
        height: 100%;

        display: flex;
        flex-direction: column;

        align-items: center;
        gap: 4rem;
    }

    .content p {
        text-align: justify;
    }

    .content>* {
        max-width: 60%;
    }


    .buttonsLayout {
        width: 60%;
        min-height: 6rem;

        display: flex;
        align-items: center;
        justify-content: center;

        gap: 1rem;
        flex-wrap: wrap;
    }

    .button {
        cursor: pointer;

        height: 3rem;
        padding-left: 1.5rem;
        padding-right: 1.5rem;

        border-radius: 1rem;

        display: grid;
        place-items: center;

        text-decoration: none;

        transition: transform .5s cubic-bezier(0, 0, 0, .9);
    }

    .button:is(:hover, :focus) {
        transform: translateY(-.1rem);
    }

    .button.solid {
        background-color: var(--ownColor);
    }

    .button.solid h4 {
        color: var(--black);
    }

    .button.weak {
        background-color: transparent;
        box-shadow: inset 0 0 0 .1rem var(--ownColor);
    }

    .button.weak h4 {
        color: var(--ownColor);
    }
</style>