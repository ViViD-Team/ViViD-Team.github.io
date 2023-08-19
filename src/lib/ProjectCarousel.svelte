<script>
    import ProjectCard from "./ProjectCard.svelte";

    import Outline from "../assets/project_covers/Outline.jpg";

    let scroller, main;

    export let projects = [
        {
            "name": "Outline",
            "description": "                                            \
                Manage your data, calculate spreadsheets and track your \
                progress using Outline! This app allows you to organize \
                text, calculations, to-do-lists and much more all in    \
                one place. The functionality is easily expandable using \
                plugins.                                                \
            ",
            "image_resource": Outline,
            "findoutmore_href": "https://github.com/AliBlubberus/OUTLINE",
            "download_href": "#"
        },
        {
            "name": "Oaftline",
            "description": "                                            \
                Manage your data, calculate spreadsheets and track your \
                progress using Outline! This app allows you to organize \
                text, calculations, to-do-lists and much more all in    \
                one place. The functionality is easily expandable using \
                plugins.                                                \
            ",
            "image_resource": Outline,
            "findoutmore_href": "https://github.com/AliBlubberus/OUTLINE",
            "download_href": null
        },
        {
            "name": "Outasdine",
            "description": "                                            \
                Manage your data, calculate spreadsheets and track your \
                progress using Outline! This app allows you to organize \
                text, calculations, to-do-lists and much more all in    \
                one place. The functionality is easily expandable using \
                plugins.                                                \
            ",
            "image_resource": Outline,
            "findoutmore_href": "https://github.com/AliBlubberus/OUTLINE",
            "download_href": null
        }
    ]

    function getCurrent() {
        let closest;
        for (let child of Array.from(scroller.children)) {
            if (!closest) {closest = child; continue;}

            if (Math.abs(child.getBoundingClientRect().left) < Math.abs(closest.getBoundingClientRect().left)) {
                closest = child;
            }
        }
        return closest;
    }

    function getPrev() {
        let arr = Array.from(scroller.children);
        let index = arr.indexOf(getCurrent()) - 1;
        if (index < 0) index = arr.length - 1;
        return arr[index];
    }

    function getNext() {
        let arr = Array.from(scroller.children);
        let index = arr.indexOf(getCurrent()) + 1;
        if (index >= arr.length) index = 0;
        return arr[index];
    }

    let currentSelected = 0;

    function update() {
        currentSelected = Array.from(scroller.children).indexOf(getCurrent());
    }
    
</script>



<main bind:this={main}>
    <div class="scroller" bind:this={scroller} on:scrollend={update}>
        {#each projects as project}
            <div class="scrollScreen">
                <ProjectCard data={project} />
            </div>
        {/each}
    </div>


    <div class="leftButtonContainer">
        <div tabindex="0" class="leftButton" on:click={function() {
            getPrev().scrollIntoView({behavior: "smooth", block: "nearest", inline: "center"});
        }}>
            <svg viewBox="0 0 18 30" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd" clip-rule="evenodd" d="M16.7678 0.732233C15.7915 -0.244078 14.2085 -0.244078 13.2322 0.732233L0.732233 13.2322C-0.244078 14.2085 -0.244078 15.7915 0.732233 16.7678L13.2322 29.2678C14.2085 30.2441 15.7915 30.2441 16.7678 29.2678C17.7441 28.2915 17.7441 26.7085 16.7678 25.7322L6.03553 15L16.7678 4.26777C17.7441 3.29146 17.7441 1.70854 16.7678 0.732233Z"/>
            </svg>
        </div>
    </div>
    <div class="rightButtonContainer">
        <div tabindex="0" class="rightButton" on:click={function() {
            getNext().scrollIntoView({behavior: "smooth", block: "nearest", inline: "center"});
        }}>
            <svg viewBox="0 0 18 30" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd" clip-rule="evenodd" d="M0.732233 0.732233C1.70854 -0.244078 3.29146 -0.244078 4.26777 0.732233L16.7678 13.2322C17.7441 14.2085 17.7441 15.7915 16.7678 16.7678L4.26777 29.2678C3.29146 30.2441 1.70854 30.2441 0.732233 29.2678C-0.244078 28.2915 -0.244078 26.7085 0.732233 25.7322L11.4645 15L0.732233 4.26777C-0.244078 3.29146 -0.244078 1.70854 0.732233 0.732233Z"/>
            </svg>
        </div>
    </div>

    <div class="indicatorContainer">
        {#if scroller}
            {#each projects as project, index}
                <div class="indicator" on:click={function() {Array.from(scroller.children)[index].scrollIntoView({behavior: "smooth", block: "nearest", inline: "center"})}}>
                    <div class="indicatorGraphic" style="
                    {currentSelected == index ? `background-color: var(--v1)` : ""}
                "></div>
                </div>
            {/each}
        {/if}
    </div>
</main>



<style>
    main {
        position: relative;
        width: 100%;
        height: 28rem;
        overflow: hidden;

        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .scroller {
        width: 100%;
        height: 24rem;

        display: flex;
        align-items: center;


        overflow-x: scroll;
        scroll-snap-type: x mandatory;
        scroll-behavior: smooth;
    }

    .scroller::-webkit-scrollbar {
        display: none;
    }

    .scrollScreen {
        width: 100%;
        height: 100%;
        display: grid;
        place-items: center;

        flex: none;

        scroll-snap-align: center;
    }

    :is(.leftButtonContainer, .rightButtonContainer) {
        cursor: pointer;

        top: 0;
        left: 0;

        position: absolute;
        height: 24rem;

        width: 5rem;
        display: grid;
        place-items: center;

        background-color: transparent;
    }

    .rightButtonContainer {
        left: unset;
        right: 0;
    }

    :is(.rightButton, .leftButton) {
        height: 3rem;
        aspect-ratio: 1 / 1;

        display: grid;
        place-items: center;

        transition: transform .5s cubic-bezier(0, 0, 0, .9);
    }

    .leftButton:is(:hover, :focus) {
        transform: translateX(-.2rem);
    }
    .rightButton:is(:hover, :focus) {
        transform: translateX(.2rem);
    }

    :is(.rightButton, .leftButton) svg {
        height: 50%;
    }

    :is(.rightButton, .leftButton) svg path {
        fill: var(--black-transparent);
        
        transition: fill .5s cubic-bezier(0, 0, 0, .9);
    }

    :is(.rightButton, .leftButton):is(:hover, :focus) svg path {
        fill: var(--black);
    }
    

    .indicatorContainer {
        width: 50%;
        flex: 1;

        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1rem;
    }

    .indicator {
        cursor: pointer;

        height: 100%;
        flex: 1;
        max-width: 5rem;

        display: grid;
        place-items: center;
    }

    .indicatorGraphic {
        height: .2rem;
        width: 100%;

        border-radius: .1rem;
        background-color: var(--black-transparent);

        transition: background-color .5s cubic-bezier(0, 0, 0, .9);
    }

    
    @media only screen and (max-width: 100vh) {
        main {
            height: 38rem;
        }

        .scroller {
            height: 36rem;

            flex-shrink: 0;
        }

        :is(.rightButtonContainer, .leftButtonContainer) {
            width: 2rem;
            height: 36rem;
        }

        :is(.leftButton, .rightButton) {
            width: 2rem;
        }

        .indicatorContainer {
            margin-bottom: 2rem;
        }
    }
</style>