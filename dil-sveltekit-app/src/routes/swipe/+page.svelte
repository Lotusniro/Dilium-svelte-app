<script>
    let dividerPosition = 50;

    function handleMouseMove(event) {
        const rect = event.currentTarget.getBoundingClientRect();
        const offsetX = event.clientX - rect.left;
        const percentage = (offsetX / rect.width) * 100;
        dividerPosition = Math.min(Math.max(percentage, 0), 100);
    }

    function handleTouchMove(event) {
        const rect = event.currentTarget.getBoundingClientRect();
        const offsetX = event.touches[0].clientX - rect.left;
        const percentage = (offsetX / rect.width) * 100;
        dividerPosition = Math.min(Math.max(percentage, 0), 100);
    }
</script>

<style>
    .container {
        position: relative;
        width: 100%;
        max-width: 600px;
        margin: 0 auto;
    }

    .image-wrapper {
        position: relative;
        width: 100%;
        overflow: hidden;
    }

    .image-wrapper img {
        display: block;
        width: 100%;
    }

    .divider {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 50%;
        width: 5px;
        background-color: #fff;
        cursor: ew-resize;
        transform: translateX(-50%);
    }

    .before {
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        overflow: hidden;
        width: var(--divider-position, 50%);
    }

    .before img {
        width: 100%;
    }
</style>

<div class="container" on:mousemove={handleMouseMove} on:touchmove={handleTouchMove}>
    <div class="image-wrapper">
        <div class="before" style="--divider-position: {dividerPosition}%;">
            <img src="/before.jpg" alt="Before">
        </div>
        <img src="/after.webp" alt="After">
        <div class="divider" style="left: {dividerPosition}%;"></div>
    </div>
</div>
