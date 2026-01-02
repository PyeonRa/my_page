<script>
    export let title = "";
</script>

<footer class="footer">
    <div class="footer-content">
        <p class="footer-text">{title}</p>
        <p class="footer-sub">AI 보조 위키 경계 설계 연구 보고서</p>
    </div>
</footer>

<style>
    .footer {
        padding: 48px 24px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        text-align: center;
    }

    .footer-content {
        max-width: 900px;
        margin: 0 auto;
    }

    .footer-text {
        margin: 0 0 8px 0;
        font-size: 18px;
        font-weight: 600;
        color: white;
    }

    .footer-sub {
        margin: 0;
        font-size: 14px;
        color: rgba(255,255,255,0.7);
    }
</style>

