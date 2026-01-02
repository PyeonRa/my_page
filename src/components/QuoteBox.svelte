<script>
    export let highlight = false;
</script>

<blockquote class="quote-box" class:highlight>
    <div class="quote-mark">"</div>
    <div class="quote-content">
        <slot />
    </div>
</blockquote>

<style>
    .quote-box {
        position: relative;
        margin: 32px 0;
        padding: 32px 32px 32px 48px;
        background: linear-gradient(135deg, #f8fafc 0%, #f0f4f8 100%);
        border-radius: 20px;
        border-left: 5px solid #2d5a87;
    }

    .quote-box.highlight {
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        border-left: none;
        color: white;
    }

    .quote-mark {
        position: absolute;
        top: 16px;
        left: 20px;
        font-size: 48px;
        font-weight: 700;
        color: #2d5a87;
        opacity: 0.3;
        line-height: 1;
        font-family: Georgia, serif;
    }

    .highlight .quote-mark {
        color: white;
        opacity: 0.2;
    }

    .quote-content {
        font-size: 18px;
        line-height: 1.8;
        font-weight: 500;
        color: #2a3a4a;
    }

    .highlight .quote-content {
        color: white;
    }

    .quote-content :global(p) {
        margin: 0;
    }
</style>

