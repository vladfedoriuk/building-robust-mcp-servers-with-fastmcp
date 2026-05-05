<template>
    <div class="three-cols-layout">
        <slot />
    </div>
</template>

<style>
.three-cols-layout {
    height: 100%;
    padding: 2rem 2.5rem;
    background-color: var(--geist-background);
    color: var(--geist-foreground);
    display: flex;
    flex-direction: column;
}

.three-cols-layout h1 {
    color: var(--geist-foreground);
    font-weight: 800;
    font-size: 2rem;
    margin: 0 0 1rem 0;
    flex-shrink: 0;
}

.three-cols-layout .cols {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    flex: 1;
    min-height: 0;
}

.three-cols-layout .col {
    display: flex;
    flex-direction: column;
    border: 1px solid var(--accents-2);
    border-radius: 6px;
    overflow: hidden;
    min-width: 0;
    background-color: var(--accents-1);
}

.three-cols-layout .col-header {
    flex: 0 0 auto;
    padding: 0.75rem 1rem 0.6rem;
    border-bottom: 1px solid var(--accents-2);
}

.three-cols-layout .col-title {
    display: block;
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--geist-foreground);
    margin-bottom: 0.2rem;
}

.three-cols-layout .col-subtitle {
    font-size: 0.68rem;
    color: var(--accents-4);
    margin: 0;
    line-height: 1.4;
}

/* code block wrapper rendered by Slidev */
.three-cols-layout .col .slidev-code,
.three-cols-layout .col > div[class^="language-"] {
    flex: 2;
    display: flex;
    flex-direction: column;
    min-height: 0;
}

.three-cols-layout .col pre {
    flex: 1;
    font-size: 0.68rem !important;
    margin: 0 !important;
    border: none !important;
    border-radius: 0 !important;
    overflow-x: auto;
    height: 100%;
}
</style>
