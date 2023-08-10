<script>
    import Blob_01 from "../assets/blob_01.svg";
    import Blob_02 from "../assets/blob_02.svg";
    import Blob_03 from "../assets/blob_03.svg";

    import ViViD from "../assets/ViViD.svg";
    import ViViD_Skelleton from "../assets/ViViD_Skelleton.svg";

    import wave_v1 from "../assets/wave_v1.svg";
    import wave_v2 from "../assets/wave_v2.svg";
    import wave_white from "../assets/wave_white.svg";

    import Separator from "./Separator.svelte";
    import MemberCard from "./MemberCard.svelte";

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
        <img src={Blob_01} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 100vh;
            left: 0vw;
        ">
        <img src={Blob_02} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 103vh;
            left: 66vw;
        ">
        <img src={Blob_03} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 110vh;
            left: 30vw;
        ">
        <img src={Blob_03} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 50vh;
            left: -30vw;
        ">
        <img src={Blob_02} class="backdropBlob" alt="asd" style="
            position: absolute;
            top: 45vh;
            left: 100vw;
        ">
    </div>

    <div class="LogoContainer">
        <img src={ViViD_Skelleton} alt="" style="animation-delay: .25s;">
        <img src={ViViD} alt="">
        <img src={ViViD_Skelleton} alt="" style="animation-delay: .25s;">
    </div>


    <div class="greetingContainer">
        <h2>Hey 👋, we’re <span class="vivid">ViViD</span>. Thanks for checking in!</h2>
    </div>

    <Separator label="Who We Are" animationDelay={.75}/>

    <div class="whoWeAreContainer">
        <p>We are two students from Germany with a passion for coding.
        In 2022, we decided to team up and cooperate on software products.</p>
    </div>

    <Separator label="Our Members"/>

    <div class="memberContainer">
        <MemberCard />
    </div>

    <div class="transition">
        <div class="wave" style="background-image: url({wave_v1});"></div>
        <div class="wave" style="background-image: url({wave_v2});"></div>
        <div class="wave" style="background-image: url({wave_white}); height: 25%; transform: translate(1px)"></div>
    </div>
</main>
  
  
  
  <style>

    @keyframes logoAppear {
        from {
            transform: translateY(-2rem);
            opacity: 0;
        }
    }
    
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


    .LogoContainer {
        margin-top: 2rem;
        margin-bottom: 2rem;

        width: 100%;
        height: 16rem;

        display: flex;
        align-items: center;
        justify-content: center;

        overflow: visible;

        gap: 2rem;
    }

    .LogoContainer img {
        height: calc(100% - 2rem);

        animation: logoAppear 2s cubic-bezier(0, 0, 0, .9) both;
    }


    .greetingContainer {
        width: 100%;
        height: 8rem;

        display: grid;
        place-items: center;

        overflow: hidden;

        animation: logoAppear 2s cubic-bezier(0, 0, 0, .9) both .5s;
    }

    .greetingContainer h2 {
        font-size: 2rem;
        font-weight: 600;
    }


    .whoWeAreContainer {
        width: 100%;

        display: grid;
        place-items: center;

        animation: logoAppear 2s cubic-bezier(0, 0, 0, .9) both 1s;
    }

    .whoWeAreContainer p {
        margin: 2rem;
        font-weight: 500;
        font-size: 1.5rem;
        text-align: center;

        width: 40%;
    }


    .memberContainer {
        width: 100%;

        display: flex;
        align-items: center;
        justify-content: center;

        flex-wrap: wrap;
    }


    .transition {
        position: relative;

        width: 100%;
        height: 5rem;
        overflow: hidden;

        transform: translateY(3px);
    }

    .transition .wave {
        position: absolute;

        bottom: 0;

        width: 100%;
        height: 100%;

        background-size: cover;
        background-repeat: repeat-x;
    }
  </style>