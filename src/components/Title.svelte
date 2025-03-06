<script>
    export let index;
    let isVisible = false;

    $: if (index === 0) {
    isVisible = true;
    } else {
    isVisible = false;
    }
</script>

<div class="title" class:visible={isVisible}>
    <h1>EVCS - OPTIM</h1>
    <p>Electric Vehicle Charging Station - Optimizing Placement Tool via Infrastructure Modeling</p>
</div>

<style>
    .title {
        position: fixed; /* Fixes the element relative to viewport, so it stays in place when scrolling */
        top: 50%; /* Positions the top edge of the element at 50% of the viewport height */
        left: 50%; /* Positions the left edge of the element at 50% of the viewport width */
        transform: translate(-50%, -50%); /* Moves the element back by 50% of its own width and height to center it perfectly */
        text-align: center; /* Aligns the text content to the center horizontally */
        opacity: 0; /* Makes the element fully transparent (invisible) initially */
        visibility: hidden; /* Hides the element from the DOM, ensuring it doesn't take up space or interact with the user */
        transition: opacity 2s, visibility 2s; /* Adds a smooth 2-second transition effect for opacity and visibility changes */
    }

    /* Status of Intro section when it is visible */
    .title.visible {
        opacity: 1;
        visibility: visible;
    }

    /* Change font size for the h1 element */
    .title h1 {
        font-size: 3rem;
    }

    /* Change font size for the p element */
    .title p {
        font-size: 1.5rem;
    }
</style>