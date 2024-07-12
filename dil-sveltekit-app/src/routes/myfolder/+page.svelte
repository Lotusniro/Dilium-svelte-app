<script>
  // Path to the image file
  const imagePath = '/cake.jpeg'; 
</script>
<div class="circular-image">
  <img src={imagePath} alt="Circular Image" />
</div>
<style>
  .circular-image {
    width: 200px; 
    height: 200px;
    border-radius: 50%;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .circular-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
</style>


