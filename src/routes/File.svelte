<script>
    let imageUrl = $state('');
    let showGrid = $state(false);
    function handleFileUpload(event) {
      const file = event.target.files[0];
      if (file) {
        imageUrl = URL.createObjectURL(file);
      }
    }
  
    onMount(() => {
        let cont = document.querySelector('.grid-box');
        for(let i=0; i < 53760; i++) {
            let y = Math.floor(i/280);
            let x = Math.round(((i / 280) - y) * 280);
            cont.insertAdjacentHTML('beforeend', `<div class="grid-item"><span class="tooltip">${x}, ${y}</span></div>`);
        }
    });

    // Clean up the object URL when component is destroyed
    import { onDestroy, onMount } from 'svelte';
    onDestroy(() => {
      if (imageUrl) {
        URL.revokeObjectURL(imageUrl);
      }
    });
  </script>
  
    <div class="top">
    <input 
      type="file" 
      accept="image/*"
      onchange={handleFileUpload}
    />
    
    <button class="grid-toggle" onclick={() => showGrid = !showGrid}>TOGGLE GRID</button>
    </div>
    <div class="grid-box {showGrid ? 'show-grid' : ''}" style="background-image:url('{imageUrl}');"></div>
 

<style>
.top {
    margin: 2vw;
}
.grid-toggle {
    cursor: pointer;
    padding: 0.5em 0.75em;
    color: white;
    background-color: #444;
    border-radius: 2px;
    font-size: 0.6em;
    letter-spacing: 0.05em;
}
.grid-toggle:hover {
    background-color: #666;
}
.grid-box {
    display: grid;
    grid-template-columns: repeat(280, 1fr);
    background: no-repeat 50% 50%;
    background-size: 100% 100%;
    height: 69vw;
}

  </style>