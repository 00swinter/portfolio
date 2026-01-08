<script>
    // In Svelte 5, children are passed as a 'snippet'
    let { children } = $props();
</script>

<div class="scroll-wrapper">
    <div class="scroll-content">
        {@render children()}
    </div>
</div>

<style>
    .scroll-wrapper {
        width: 100%;
        overflow: hidden; /* Clips any messy shadows or edges */
    }

    .scroll-content {
        display: flex;
        gap: 2rem;
        padding: 50px; /* Big padding so card shadows don't get cut off */
        
        overflow-x: auto;
        scroll-snap-type: x mandatory;
        scroll-behavior: smooth;

        /* Hide scrollbars */
        -ms-overflow-style: none;
        scrollbar-width: none;
    }

    .scroll-content::-webkit-scrollbar {
        display: none;
    }

    /* Adds a "spacer" at the end so the last item isn't flush against the edge */
    .scroll-content::after {
        content: '';
        flex: 0 0 50px;
    }
</style>