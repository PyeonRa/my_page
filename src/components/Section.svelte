<script>
    export let number = "";
    export let title = "";
    export let accent = false;
</script>

<section class="section" class:accent>
    <div class="section-inner">
        <div class="section-header">
            {#if number}
                <span class="section-number">{number}</span>
            {/if}
            <h2 class="section-title">{title}</h2>
        </div>
        <div class="section-content">
            <slot />
        </div>
    </div>
</section>

<style>
    .section {
        padding: 60px 24px;
        background: #fafbfc;
    }

    .section.accent {
        background: linear-gradient(180deg, #f0f4f8 0%, #fafbfc 100%);
    }

    .section-inner {
        max-width: 900px;
        margin: 0 auto;
    }

    .section-header {
        display: flex;
        align-items: center;
        gap: 16px;
        margin-bottom: 32px;
    }

    .section-number {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 48px;
        height: 48px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        font-size: 18px;
        font-weight: 800;
        border-radius: 14px;
        flex-shrink: 0;
    }

    .section-title {
        margin: 0;
        font-size: 28px;
        font-weight: 700;
        color: #1a2a3a;
        letter-spacing: -0.5px;
    }

    .section-content {
        color: #3a4a5a;
        font-size: 17px;
        line-height: 1.8;
    }

    .section-content :global(p) {
        margin: 0 0 20px 0;
    }

    .section-content :global(p:last-child) {
        margin-bottom: 0;
    }

    .section-content :global(strong) {
        color: #1a2a3a;
        font-weight: 600;
    }

    .section-content :global(ul),
    .section-content :global(ol) {
        margin: 0 0 20px 0;
        padding-left: 0;
        list-style: none;
    }

    .section-content :global(li) {
        position: relative;
        padding-left: 28px;
        margin-bottom: 12px;
    }

    .section-content :global(li::before) {
        content: '';
        position: absolute;
        left: 0;
        top: 10px;
        width: 8px;
        height: 8px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        border-radius: 50%;
    }
</style>

