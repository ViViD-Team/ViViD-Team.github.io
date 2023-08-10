<script>
    import Blob_01 from "../assets/blob_01.svg";
    import Blob_02 from "../assets/blob_02.svg";
    import Blob_03 from "../assets/blob_03.svg";

    import wave_v1 from "../assets/wave_v1.svg";
    import wave_v2 from "../assets/wave_v2.svg";
    import wave_white from "../assets/wave_white.svg";

    import Separator from "./Separator.svelte";
    import BlogPost from "./BlogPost.svelte";

    const blogPosts = [
        {},
        {},
        {},
        {},
        {},
        {},
        {}
    ]

</script>



<main>
    <div class="background">
        <img src={Blob_01} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 2vh;
            left: -10vw;
        ">
        <img src={Blob_01} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 25vh;
            left: 63vw;
        ">
        <img src={Blob_03} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 30vh;
            left: 45vw;
        ">
        <img src={Blob_02} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 40vh;
            left: 20vw;
        ">
        <img src={Blob_03} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: -15vh;
            left: 33vw;
        ">
        <img src={Blob_03} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: -20vh;
            left: 80vw;
        ">
    </div>

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
        <div class="wave" style="background-image: url({wave_white}); height: 25%; transform: translate(1px)"></div>
    </div>

</main>



<style>
    main {
        position: relative;

        width: 100vw;
        min-height: 80vh;

        display: flex;
        flex-direction: column;

        overflow: hidden;
    }
  
    .background {
        z-index: 0;
        position: absolute;

        top: 0;
        left: 0;

        width: 100%;
        height: 100%;

        overflow: hidden;

        opacity: .3;

        user-select: none;
        -webkit-user-drag: none;
    }
  
    .backdropBlob {
        width: 30vw;
        height: 30vw;

        filter: blur(20vh);
        -webkit-filter: blur(20vh);

        user-select: none;
        -webkit-user-drag: none;
    }


    .transition {
        position: relative;

        width: 100%;
        height: 5rem;
        overflow: hidden;
    }

    .transition.intro {
        transform: scale(-1, -1);
    }

    .transition .wave {
        position: absolute;

        bottom: 0;

        width: 100%;
        height: 100%;

        background-size: cover;
        background-repeat: repeat-x;
    }


    .blogPostLayout {
        margin-bottom: 2rem;

        width: calc(100% - 4rem);
        padding-left: 2rem;
        padding-right: 2rem;

        display: flex;
        align-items: center;
        justify-content: center;

        flex-wrap: wrap;
    }
</style>