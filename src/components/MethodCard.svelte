<script>
    export let id = "";
    export let title = "";
    export let description = "";
    export let features = [];
</script>

<div class="method-card">
    <div class="method-badge">{id}</div>
    <h3 class="method-title">{title}</h3>
    <p class="method-desc">{description}</p>
    {#if features.length > 0}
        <ul class="method-features">
            {#each features as feature}
                <li>{feature}</li>
            {/each}
        </ul>
    {/if}
</div>

<style>
    .method-card {
        background: white;
        border-radius: 20px;
        padding: 32px;
        box-shadow: 0 4px 20px rgba(0,0,0,0.06);
        border: 1px solid #e8eef3;
        text-align: center;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .method-card:hover {
        transform: translateY(-6px);
        box-shadow: 0 16px 40px rgba(30,58,95,0.15);
    }

    .method-badge {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 56px;
        height: 56px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        font-size: 22px;
        font-weight: 800;
        border-radius: 16px;
        margin-bottom: 20px;
        box-shadow: 0 4px 12px rgba(30,58,95,0.3);
    }

    .method-title {
        margin: 0 0 12px 0;
        font-size: 22px;
        font-weight: 700;
        color: #1a2a3a;
    }

    .method-desc {
        margin: 0 0 20px 0;
        font-size: 15px;
        color: #5a6a7a;
        line-height: 1.6;
    }

    .method-features {
        list-style: none;
        padding: 0;
        margin: 0;
        text-align: left;
    }

    .method-features li {
        position: relative;
        padding: 10px 0 10px 28px;
        font-size: 14px;
        color: #4a5a6a;
        border-top: 1px solid #f0f4f8;
    }

    .method-features li:first-child {
        border-top: none;
    }

    .method-features li::before {
        content: '✓';
        position: absolute;
        left: 0;
        color: #2d5a87;
        font-weight: 700;
    }
</style>

