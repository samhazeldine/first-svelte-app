<script>
    import { fade } from "svelte/transition";

    const images = [
        "http://placekitten.com/700",
        "http://placekitten.com/600",
        "http://placekitten.com/500",
    ];

    let imageIndex = 0;

    function nextImage() {
        imageIndex = (imageIndex + 1) % images.length;
    }
</script>

<div id="cascade">

    {#key imageIndex}
        <img id="cascade__img"  src={images[imageIndex]} alt="alt" transition:fade="{{duration:1000}}"/>
    {/key}

    <button id="cascade__right" on:click={nextImage}> right </button>
    <button id="cascade__left" on:click={nextImage}> left </button>
</div>

<p>test</p>

<style>
    #cascade {
        position:relative;
    }

    #cascade__img {
        position:absolute;
        max-width:80%;
    }

    #cascade__right, 
    #cascade__left {
        position:absolute;
        top:50%;
        transform:translateY(-50%);
        cursor:pointer;
    }

    #cascade__right {
        right:5px;
    }
    
    #cascade__left {
        left:5px;
    }

  
</style>