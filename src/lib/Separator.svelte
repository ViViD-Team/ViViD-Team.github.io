<script>
    export let label = "";

    export let animationDelay = 0;
</script>



<main>
    <div class="dash left" style="animation-delay: {animationDelay}s;"></div>
    <h3 style="animation-delay: {animationDelay}s;">{label}</h3>
    <div class="dash right" style="animation-delay: {animationDelay}s;"></div>
</main>



<style>

    @keyframes panInLeft {
        from {
            transform: translateX(-1rem);
            opacity: 0;
        }
    }

    @keyframes panInRight {
        from {
            transform: translateX(1rem);
            opacity: 0;
        }
    }

    @keyframes appear {
        from {
            opacity: 0;
        }
    }

    .left {
        animation: panInLeft 2s cubic-bezier(0, 0, 0, .9) both;
    }

    .right {
        animation: panInRight 2s cubic-bezier(0, 0, 0, .9) both;
    }

    main {
        margin-top: 4rem;
        margin-bottom: 2rem;

        width: 100%;
        height: 2rem;

        display: flex;
        align-items: center;
        justify-content: space-evenly;

        pointer-events: none;
    }

    .dash {
        height: .15rem;
        flex: 1;

        margin-left: 1rem;
        margin-right: 1rem;

        border-radius: .125rem;
        background-color: var(--white);
    }

    h3 {
        font-size: 1.2rem;
        color: var(--v3);

        letter-spacing: .1rem;
        font-weight: 900;

        pointer-events: all;

        animation: appear 2s cubic-bezier(0, 0, 0, .9) both;
    }
</style>