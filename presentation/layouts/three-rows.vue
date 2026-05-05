<template>
    <div class="three-rows-layout">
        <slot />
    </div>
</template>

<style>
.three-rows-layout {
    height: 100%;
    padding: 2rem 2.5rem;
    background-color: var(--geist-background);
    color: var(--geist-foreground);
    display: flex;
    flex-direction: column;
    gap: 0;
}

.three-rows-layout h1 {
    color: var(--geist-foreground);
    font-weight: 800;
    font-size: 2rem;
    margin: 0 0 0.75rem 0;
    flex-shrink: 0;
}

.three-rows-layout .rows {
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
    flex: 1;
    min-height: 0;
}

.three-rows-layout .row {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 0;
    flex: 1;
    min-height: 0;
    border: 1px solid var(--accents-2);
    border-radius: 6px;
    overflow: hidden;
    background-color: var(--accents-1);
}

.three-rows-layout .row-label {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0.75rem 1rem;
    border-right: 1px solid var(--accents-2);
    background-color: var(--accents-1);
}

.three-rows-layout .row-title {
    display: block;
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--geist-foreground);
    margin-bottom: 0.25rem;
}

.three-rows-layout .row-subtitle {
    font-size: 0.68rem;
    color: var(--accents-4);
    margin: 0;
    line-height: 1.4;
}

/* code block wrapper rendered by Slidev */
.three-rows-layout .row-code {
    display: flex;
    flex-direction: column;
    min-height: 0;
    min-width: 0;
}

.three-rows-layout .row-code .slidev-code,
.three-rows-layout .row-code > div[class^="language-"] {
    flex: 1;
    display: flex;
    flex-direction: column;
    min-height: 0;
}

.three-rows-layout .row-code pre {
    flex: 1;
    font-size: 0.68rem !important;
    margin: 0 !important;
    border: none !important;
    border-radius: 0 !important;
    overflow: hidden;
    height: 100%;
    zoom: 0.78;
}
</style>
