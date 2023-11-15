<script>
    import BlobBackground from "../assets/blobBackground.svg"; 


    import ViViD from "../assets/ViViD.svg";
    import ViViD_Skelleton from "../assets/ViViD_Skelleton.svg";

    import wave_v1 from "../assets/wave_v1.svg";
    import wave_v2 from "../assets/wave_v2.svg";
    import wave_white from "../assets/wave_white.svg";

    import Separator from "./Separator.svelte";
    import MemberCard from "./MemberCard.svelte";

    const members = [
        {
            "name": "Adrian",
            "profilePictureResource": "url(\"https://avatars.githubusercontent.com/u/87329737?v=4\")",
            "aboutMe": "I'm an 18 year old german student. During fifth grade, I had my first bit of programming experience with scratch. Around 2018 I tried developing games in unity. Today, I mainly do frontend / webdesign. I am most comfortable in javascript, though I'm also currently learning rust and c++.",
            "social": {
                "email": "adrian.juengling@gmail.com",
                "github": "https://github.com/AliBlubberus",
            }
        },
        {
            "name": "Jan",
            "profilePictureResource": "url(\"https://avatars.githubusercontent.com/u/85286163?v=4\")",
            "aboutMe": "I'm a 17 year old student from Germany. I started coding in about 2018 in Python, which I used for almost four years before learning Rust. I now do backend stuff in Rust and rely on Adrian for any frontend that's supposed to look cool.",
            "social": {
                "email": "jan.neuenfeld@gmail.com",
                "github": "https://github.com/JanNeuenfeld",
            }
        }
    ];

</script>
  
  
  
<main>
    <div class="patternBackground" style="background-image: url({BlobBackground});"></div>

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

    <Separator label="Our Members" animationDelay={1.25}/>

    <div class="memberContainer">
        {#each members as member}
            <MemberCard data={member}/>
        {/each}
    </div>

    <div class="transition">
        <div class="wave" style="background-image: url({wave_v1});"></div>
        <div class="wave" style="background-image: url({wave_v2});"></div>
        <div class="wave" style="background-image: url({wave_white}); height: 25%;"></div>
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
  
    .patternBackground {
        position: absolute;

        top: 0;
        left: 0;

        width: 100%;
        height: 100%;

        background-size: cover;
        filter: blur(15vh);
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
        min-height: 8rem;

        display: grid;
        place-items: center;

        overflow: hidden;

        animation: logoAppear 2s cubic-bezier(0, 0, 0, .9) both .5s;
    }

    .greetingContainer h2 {
        max-width: 80%;

        font-size: 2rem;
        font-weight: 600;

        text-align: center;
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

        animation: logoAppear 2s cubic-bezier(0, 0, 0, .9) both 1.5s;
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
        left: -1px;

        width: 105%;
        height: 100%;

        background-size: cover;
        background-repeat: repeat-x;
    }

    
    @media only screen and (max-width: 100vh) {
        .LogoContainer {
            height: 8rem;
        }

        .whoWeAreContainer p {
            width: 80%;
            font-size: 1.25rem;
        }

        .memberContainer {
            padding: 2rem;

            width: calc(100vw - 4rem);

            flex-direction: row;
            flex-wrap: nowrap;

            justify-content: flex-start;
            gap: 2rem;

            overflow-x: scroll;
            flex-shrink: 0;
            flex-grow: 0;
        }
    }
  </style>