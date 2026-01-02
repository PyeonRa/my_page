<script>
    export let icon = "";
    export let title = "";
    export let description = "";
</script>

<div class="metric-item">
    <div class="metric-icon">{icon}</div>
    <div class="metric-content">
        <h4 class="metric-title">{title}</h4>
        <p class="metric-desc">{description}</p>
    </div>
</div>

<style>
    .metric-item {
        display: flex;
        align-items: flex-start;
        gap: 16px;
        padding: 20px;
        background: white;
        border-radius: 16px;
        border: 1px solid #e8eef3;
        transition: box-shadow 0.2s ease;
    }

    .metric-item:hover {
        box-shadow: 0 4px 16px rgba(0,0,0,0.08);
    }

    .metric-icon {
        flex-shrink: 0;
        width: 48px;
        height: 48px;
        display: flex;
        align-items: center;
        justify-content: center;
        background: linear-gradient(135deg, #e8f4fd 0%, #d0e8f8 100%);
        border-radius: 12px;
        font-size: 22px;
    }

    .metric-content {
        flex: 1;
    }

    .metric-title {
        margin: 0 0 6px 0;
        font-size: 16px;
        font-weight: 700;
        color: #1a2a3a;
    }

    .metric-desc {
        margin: 0;
        font-size: 14px;
        color: #5a6a7a;
        line-height: 1.5;
    }
</style>

