<script context="module">
  export const prerender = true;
</script>

<script>
  let sliderValue = 50;

  function handleInput(event) {
    sliderValue = event.target.value;
  }
</script>

<svelte:head>
  <title>Image Comparison Slider | My Awesome Site</title>
  <meta name="description" content="Compare before and after images using this interactive slider. See the transformation at a glance.">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta property="og:title" content="Image Comparison Slider | My Awesome Site">
  <meta property="og:description" content="Compare before and after images using this interactive slider. See the transformation at a glance.">
  <meta property="og:image" content="/before.jpg">
  <meta property="og:url" content="https://www.myawesomesite.com/slider">
  <meta name="twitter:card" content="summary_large_image">

  <script type="application/ld+json">
    {
      "@context": "https://schema.org",
      "@type": "WebPage",
      "name": "Image Comparison Slider",
      "description": "Compare before and after images using this interactive slider. See the transformation at a glance.",
      "url": "https://www.myawesomesite.com/slider",
      "image": "https://www.myawesomesite.com/before.jpg"
    }
  </script>
</svelte:head>

<style>
  html {
    box-sizing: border-box;
  }
  *, *:before, *:after {
    box-sizing: inherit;
  }

  body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    position: relative;
    width: 900px;
    height: 600px;
    border: 2px solid white;
  }
  .img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-size: 900px 100%;
  }
  .background-img {
    background-image: url('/before.jpg');
   
  }
  .foreground-img {
    background-image: url('/after.webp');
    width: var(--slider-width);
  }
  .slider {
    position: absolute;
    -webkit-appearance: none;
    appearance: none;
    width: 100%;
    height: 100%;
    background: rgba(242, 242, 242, .3);
    outline: none;
    margin: 0;
    transition: all .2s;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .slider:hover {
    background: rgba(242, 242, 242, .1);
  }
  .slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 6px;
    height: 600px;
    background: white;
    cursor: pointer;
  }
  .slider::-moz-range-thumb {
    width: 6px;
    height: 600px;
    background: white;
    cursor: pointer;
  }
  .slider-button {
    --size: 30px;
    pointer-events: none;
    position: absolute;
    width: var(--size);
    height: var(--size);
    border-radius: 50%;
    background-color: white;
    left: calc(var(--slider-value) - 15px);
    top: calc(50% - 15px);
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>

<div class='container'>
  <div class='img background-img'  alt="Before Image"></div>
  <div class='img foreground-img' style="--slider-width: {sliderValue}%;" alt="After Image"></div>
  <input type="range" min="1" max="100" bind:value={sliderValue} class="slider" on:input={handleInput} />
  <div class='slider-button' style="--slider-value: {sliderValue}%;"></div>
</div>
