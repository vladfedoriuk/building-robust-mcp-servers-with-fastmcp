<template>
    <div class="section-layout">
        <div class="section-inner">
            <slot />
        </div>
    </div>
</template>

<style>
.section-layout {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    background-color: var(--geist-background);
}

.section-inner {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
    padding: 0 4rem;
    text-align: center;
}


.section-layout h1 {
    color: var(--geist-foreground);
    font-size: 3rem;
    font-weight: 800;
    line-height: 1.15;
    letter-spacing: -0.02em;
    margin: 0;
}
</style>
