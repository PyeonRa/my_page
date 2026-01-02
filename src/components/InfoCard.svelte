<script>
    export let title = "";
    export let icon = "";
    export let variant = "default"; // default, primary, highlight
</script>

<div class="info-card" class:primary={variant === 'primary'} class:highlight={variant === 'highlight'}>
    {#if icon}
        <div class="card-icon">{icon}</div>
    {/if}
    <div class="card-content">
        {#if title}
            <h3 class="card-title">{title}</h3>
        {/if}
        <div class="card-body">
            <slot />
        </div>
    </div>
</div>

<style>
    .info-card {
        background: white;
        border-radius: 20px;
        padding: 28px;
        box-shadow: 0 4px 20px rgba(0,0,0,0.06);
        border: 1px solid #e8eef3;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .info-card:hover {
        transform: translateY(-4px);
        box-shadow: 0 12px 32px rgba(0,0,0,0.1);
    }

    .info-card.primary {
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        border: none;
        color: white;
    }

    .info-card.highlight {
        background: linear-gradient(135deg, #f8fafc 0%, #e8f4fd 100%);
        border: 2px solid #2d5a87;
    }

    .card-icon {
        font-size: 36px;
        margin-bottom: 16px;
    }

    .card-title {
        margin: 0 0 12px 0;
        font-size: 20px;
        font-weight: 700;
        color: #1a2a3a;
    }

    .primary .card-title {
        color: white;
    }

    .card-body {
        font-size: 15px;
        line-height: 1.7;
        color: #4a5a6a;
    }

    .primary .card-body {
        color: rgba(255,255,255,0.9);
    }

    .card-body :global(p) {
        margin: 0 0 12px 0;
    }

    .card-body :global(p:last-child) {
        margin-bottom: 0;
    }
</style>

