<script>
    import BlobBackground from "../assets/blobBackground.svg"; 

    import wave_v1 from "../assets/wave_v1.svg";
    import wave_v2 from "../assets/wave_v2.svg";
    import wave_white from "../assets/wave_white.svg";

    import Separator from "./Separator.svelte";
    import BlogPost from "./BlogPost.svelte";

    const blogPosts = [
        /* {
            "title": "Test Article",
            "id": "test",
            "imageResource": "/src/assets/project_covers/Outline.jpg"
        } */
    ]

</script>



<main>
    <div class="patternBackground" style="background-image: url({BlobBackground});"></div>

    <div class="transition intro">
        <div class="wave" style="background-image: url({wave_v1});"></div>
        <div class="wave" style="background-image: url({wave_v2});"></div>
        <div class="wave" style="background-image: url({wave_white}); height: 25%; transform: translate(1px)"></div>
    </div>

    <Separator label="What We're Up To"/>

    <div class="blogPostLayout">
        {#each blogPosts as post}
            <BlogPost data={post}/>
        {/each}
    </div>

    <div class="transition">
        <div class="wave" style="background-image: url({wave_v1});"></div>
        <div class="wave" style="background-image: url({wave_v2});"></div>
        <div class="wave" style="background-image: url({wave_white}); height: 25%;"></div>
    </div>

</main>



<style>
    main {
        position: relative;

        width: 100vw;

        display: flex;
        flex-direction: column;

        overflow: hidden;
    }
  
    .patternBackground {
        position: absolute;

        top: 0;
        left: 0;

        width: 100%;
        height: 100%;

        background-size: cover;
        filter: blur(15vh);
    }


    .transition {
        position: relative;

        width: 100%;
        height: 5rem;
        overflow: hidden;
    }

    .transition.intro {
        transform: scale(-1, -1) translateY(1px);
    }

    .transition .wave {
        position: absolute;

        bottom: 0;
        left: -1px;

        width: 105%;
        height: 100%;

        background-size: cover;
        background-repeat: repeat-x;
    }


    .blogPostLayout {
        margin-bottom: 4rem;

        width: calc(100% - 4rem);
        padding-left: 2rem;
        padding-right: 2rem;

        display: flex;
        align-items: center;
        justify-content: center;

        flex-wrap: wrap;
    }

    @media only screen and (max-width: 100vh) {
        .blogPostLayout {
            padding: 2rem;

            height: 30rem;
            gap: 2rem;

            flex-direction: column;

            justify-content: flex-start;

            overflow-x: scroll;
        }
    }
</style>