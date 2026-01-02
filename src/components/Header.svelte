<script>
    export let title = "";
    export let subtitle = "";
    export let badge = "";
</script>

<header class="header">
    <div class="header-bg"></div>
    <div class="header-content">
        {#if badge}
            <div class="header-badge">{badge}</div>
        {/if}
        <h1 class="header-title">{title}</h1>
        {#if subtitle}
            <p class="header-subtitle">{subtitle}</p>
        {/if}
    </div>
    <div class="header-wave">
        <svg viewBox="0 0 1440 120" preserveAspectRatio="none">
            <path d="M0,64 C480,150 960,-20 1440,64 L1440,120 L0,120 Z" fill="#fafbfc"/>
        </svg>
    </div>
</header>

<style>
    .header {
        position: relative;
        padding: 80px 24px 100px;
        overflow: hidden;
    }

    .header-bg {
        position: absolute;
        inset: 0;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 50%, #3d7ab5 100%);
        z-index: 0;
    }

    .header-bg::before {
        content: '';
        position: absolute;
        inset: 0;
        background: 
            radial-gradient(circle at 20% 30%, rgba(255,255,255,0.1) 0%, transparent 50%),
            radial-gradient(circle at 80% 70%, rgba(255,255,255,0.08) 0%, transparent 40%);
    }

    .header-content {
        position: relative;
        z-index: 1;
        max-width: 900px;
        margin: 0 auto;
        text-align: center;
        color: white;
    }

    .header-badge {
        display: inline-block;
        padding: 10px 20px;
        background: rgba(255,255,255,0.15);
        backdrop-filter: blur(10px);
        border: 1px solid rgba(255,255,255,0.2);
        border-radius: 30px;
        font-size: 14px;
        font-weight: 600;
        letter-spacing: 0.5px;
        margin-bottom: 24px;
    }

    .header-title {
        margin: 0 0 20px 0;
        font-size: clamp(32px, 5vw, 52px);
        font-weight: 800;
        line-height: 1.2;
        letter-spacing: -1px;
        text-shadow: 0 2px 20px rgba(0,0,0,0.2);
    }

    .header-subtitle {
        margin: 0;
        font-size: clamp(16px, 2.5vw, 20px);
        opacity: 0.9;
        line-height: 1.6;
        max-width: 700px;
        margin: 0 auto;
    }

    .header-wave {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        z-index: 2;
    }

    .header-wave svg {
        display: block;
        width: 100%;
        height: 60px;
    }
</style>

