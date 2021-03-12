<script>
    import { fade } from "svelte/transition";

    const images = [
        "http://placekitten.com/200/200",
        "http://placekitten.com/202/202",
        "http://placekitten.com/201/201",
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

    <button class="fas fa-camera" on:click={nextImage}></button>
</div>

<style>
    #cascade {
        position:relative;
        height: 200px;
    }
    #cascade__img {
        position:absolute;
    }
    button {
        position:absolute;
    }
</style>