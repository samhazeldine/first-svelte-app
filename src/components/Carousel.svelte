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
    {#each [images[imageIndex]] as image (imageIndex)}
        <img id="cascade__img"  src={image} alt="alt" transition:fade="{{duration:1000}}"/>
    {/each}
</div>

<button on:click={nextImage}> Next Image </button>

<p> I want this below</p>

<style>
    #cascade {
        position:relative;
    }
    #cascade__img {
        position:absolute;
    }
    button{
        position:relative;
    }
</style>
