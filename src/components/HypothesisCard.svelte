<script>
    export let number = "";
    export let text = "";
</script>

<div class="hypothesis-card">
    <div class="hypothesis-number">가설 {number}</div>
    <p class="hypothesis-text">{text}</p>
</div>

<style>
    .hypothesis-card {
        background: white;
        border-radius: 16px;
        padding: 24px 28px;
        box-shadow: 0 2px 12px rgba(0,0,0,0.05);
        border: 1px solid #e8eef3;
        display: flex;
        align-items: flex-start;
        gap: 20px;
        transition: transform 0.2s ease;
    }

    .hypothesis-card:hover {
        transform: translateX(8px);
    }

    .hypothesis-number {
        flex-shrink: 0;
        padding: 8px 16px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        font-size: 13px;
        font-weight: 700;
        border-radius: 20px;
        white-space: nowrap;
    }

    .hypothesis-text {
        margin: 0;
        font-size: 16px;
        line-height: 1.7;
        color: #3a4a5a;
    }
</style>

