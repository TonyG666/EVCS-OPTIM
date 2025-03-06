<script>
    export let index;
    let isVisible = false;

    $: if (index === 1) {
    isVisible = true;
    } else {
    isVisible = false;
    }
</script>

<div class="background" class:visible={isVisible}>
    <p>With the growing emphasis on clean transportation, there has been a significant increase in electric vehicles (EVs). To accommodate for this growth, there needs to be an expansion of EV charging stations. 
        EV-OPTIM aims to find the most optimal parking lots for new EV charging within San Diego County.
    </p>
</div>

<style>
    .background {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        text-align: center;
        opacity: 0;
        visibility: hidden;
        transition: opacity 2s, visibility 2s;
    }

    /* Status of Intro section when it is visible */
    .background.visible {
        opacity: 1;
        visibility: visible;
    }

    /* Change font size for the p element */
    .background p {
        font-size: 1.5rem;
    }
</style>