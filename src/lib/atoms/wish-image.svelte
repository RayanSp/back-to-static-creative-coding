<script>
    export let wish

    import { Title, Image, LinkImage, TitleBeschrijving } from '$lib/index.js'

    import { onMount } from 'svelte';
        onMount(() => {

    document.addEventListener("DOMContentLoaded", function() {
  const originalImage = document.getElementById("originalImage");
  const risoCanvas = document.getElementById("risoCanvas");
  const ctx = risoCanvas.getContext("2d");

  // Set canvas size to match the original image
  risoCanvas.width = originalImage.width;
  risoCanvas.height = originalImage.height;

  // Draw the original image on the canvas
  ctx.drawImage(originalImage, 0, 0, risoCanvas.width, risoCanvas.height);

  // Apply the risoprint effect using CSS filters
  risoCanvas.style.filter = "contrast(1.2) brightness(1.2) saturate(1.5) blur(0.5px)";

  // Optionally, you can add more adjustments or use a library for better effects
});
});


</script>

<div class="risoprint-container">
<img src={wish.image.url} width={wish.image.width} height={wish.image.height} id="originalImage" alt="Afbeelding van {wish.heading}" />
<canvas id="risoCanvas"></canvas>
</div>

<style>
    img {
        width: clamp(100%, 100%, 12rem); 
        background-color: var(--color-accent-100);  
        height: auto;
        aspect-ratio: 1/1;
        object-fit: cover;
        margin-bottom: var(--unit-small);
    }

    .risoprint-container {
        position: relative;
    }   

    #originalImage {
        display: block;
        max-width: 100%;
        height: auto;
    }

    #risoCanvas {
        position: absolute;
        top: 0;
        left: 0;
    }
</style>