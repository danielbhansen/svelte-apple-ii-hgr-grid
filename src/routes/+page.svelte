<script>
    import '../style.css';
    import File from './File.svelte';
</script>
<div class="top">
    <h1>Apple II HGR2 Grid</h1>
    <p>Upload an image you want to map to the Apple II HGR2 high resolution graphics mode as an overlaid grid. </p>
    <p>HGR2 resolution is 280 x 192. Upload an image with a 7:5 aspect ratio for best results.</p>
    <p>If you prefer, you can run the app locally by cloning the repo and doing a local Svelte build: <a target="_blank" href="https://github.com/danielbhansen/svelte-apple-ii-hgr-grid">https://github.com/danielbhansen/svelte-apple-ii-hgr-grid</a></p>
</div>
<File />
<style>
.top {
    margin: 2vw;
}
</style>