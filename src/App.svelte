<script>
    import Header from './components/Header.svelte';
    import ExperimentPanel from './components/ExperimentPanel.svelte';
    import Footer from './components/Footer.svelte';
</script>

<div class="page">
    <Header 
        badge="연구 보고서"
        title="AI 보조 위키에서의 경계 설계에 관한 후속 탐구"
        subtitle="'도움'과 '대신 작성'을 구분하는 실험적 분석"
    />

    <main class="main">
        <!-- 1. 연구 배경 -->
        <section class="section">
            <div class="section-header">
                <span class="section-num">1</span>
                <h2>연구 배경</h2>
            </div>
            <p>
                최근 인공지능은 문서 작성에 있어 인간의 능력을 빠르게 대체하고 있다. 
                대규모 언어 모델은 위키 문서를 짧은 시간 안에 생성할 수 있으며, 이는 정보 생산의 효율을 크게 높인다. 
                그러나 이러한 변화는 위키의 본질에 대한 근본적인 질문을 제기한다.
            </p>
            <blockquote>
                위키는 단순한 정보 저장소가 아니라, 사람이 직접 쓰고 서로 검증하는 과정을 통해 신뢰를 형성해 온 지식 시스템이다.
            </blockquote>
            <p>
                AI가 문서를 대신 작성하면, 사용자는 지식의 생산자가 아닌 소비자로 전락할 수 있다. 
                본 연구는 <strong>'AI 보조'와 'AI 대체'의 경계</strong>를 실험적으로 구분하는 것을 출발점으로 삼는다.
            </p>
        </section>

        <!-- 2. 연구 목적 & 질문 -->
        <section class="section alt">
            <div class="two-col">
                <div>
                    <div class="section-header">
                        <span class="section-num">2</span>
                        <h2>연구 목적</h2>
                    </div>
                    <ul class="compact-list">
                        <li>AI 개입 수준에 따른 문서 품질과 작성자 인식 변화 분석</li>
                        <li>주도권, 책임감, 학습 효과와 AI 개입의 관계 검증</li>
                        <li>'AI 초안 작성이 항상 효율적'이라는 가정의 비판적 검토</li>
                    </ul>
                </div>
                <div>
                    <div class="section-header">
                        <span class="section-num">3</span>
                        <h2>연구 질문</h2>
                    </div>
                    <ul class="compact-list">
                        <li><strong>Q1.</strong> AI 개입 수준이 달라질 때 문서의 정확성과 출처 품질은?</li>
                        <li><strong>Q2.</strong> 어느 지점부터 "내가 쓴 것이 아니다"라고 인식하는가?</li>
                        <li><strong>Q3.</strong> AI 보조가 학습 효과를 저해하는가, 강화하는가?</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- 3. 연구 가설 -->
        <section class="section">
            <div class="section-header">
                <span class="section-num">4</span>
                <h2>연구 가설</h2>
            </div>
            <div class="hypothesis-row">
                <div class="hypothesis-card">
                    <span class="h-num">가설 1</span>
                    <p>AI 보조(편집·검증 지원)는 문서 정확성과 출처 품질을 향상시킨다.</p>
                </div>
                <div class="hypothesis-card">
                    <span class="h-num">가설 2</span>
                    <p>AI 초안 작성 시, 작성 시간은 단축되지만 주도권과 학습 효과는 감소한다.</p>
                </div>
                <div class="hypothesis-card">
                    <span class="h-num">가설 3</span>
                    <p>AI 개입이 일정 수준을 넘으면 부작용(책임 약화)이 더 커진다.</p>
                </div>
            </div>
        </section>

        <!-- 4. 연구 방법 -->
        <section class="section alt">
            <div class="section-header">
                <span class="section-num">5</span>
                <h2>연구 방법</h2>
            </div>
            <p class="section-desc">동일한 주제의 위키 문서를 세 개의 그룹이 작성한다. 모든 그룹은 동일한 시간 제한과 참고 자료 접근 권한을 가진다.</p>
            
            <div class="method-row">
                <div class="method-card">
                    <div class="method-badge">G1</div>
                    <strong>AI 없음</strong>
                    <p>인간만으로 작성하는 통제 그룹</p>
                    <small>직접 자료 조사 · 온전한 저자 경험</small>
                </div>
                <div class="method-card">
                    <div class="method-badge">G2</div>
                    <strong>AI 보조</strong>
                    <p>편집과 검증을 돕는 보조 도구</p>
                    <small>맞춤법 교정 · 문장 다듬기 · 출처 제안</small>
                </div>
                <div class="method-card">
                    <div class="method-badge">G3</div>
                    <strong>AI 초안 허용</strong>
                    <p>AI가 초안 생성, 인간이 수정</p>
                    <small>빠른 작성 · 수정/보완 중심</small>
                </div>
            </div>

            <h3 class="sub-title">평가 지표</h3>
            <div class="metrics-row">
                <span class="metric">🎯 정확성 (오류 수)</span>
                <span class="metric">📚 출처 품질</span>
                <span class="metric">⏱️ 작성 효율</span>
                <span class="metric">✋ 주도권 인식</span>
                <span class="metric">🧠 학습 효과</span>
            </div>
        </section>

        <!-- 5. 실험 체험 -->
        <section class="section">
            <div class="section-header">
                <span class="section-num">⚡</span>
                <h2>직접 체험해보기</h2>
            </div>
            <ExperimentPanel />
        </section>

        <!-- 6. 분석 및 결과 -->
        <section class="section alt">
            <div class="section-header">
                <span class="section-num">6</span>
                <h2>분석 및 결과</h2>
            </div>
            
            <div class="analysis-row">
                <div class="analysis-card good">
                    <strong>G2 (보조)</strong>
                    <p>오류 감소, 출처 품질 개선에서 안정적 성과. 주도권과 학습 효과 유지.</p>
                </div>
                <div class="analysis-card warn">
                    <strong>G3 (초안)</strong>
                    <p>시간 단축은 장점이나, 내용 이해 없이 수정만 참여할 위험. 책임감 감소.</p>
                </div>
            </div>

            <blockquote class="highlight">
                AI는 문서를 대신 써줄 때 가장 편리하지만, <strong>위키를 건강하게 만들 때는 사람이 쓰도록 도울 때 가장 효과적이다.</strong>
            </blockquote>
        </section>

        <!-- 7. 핵심 발견 -->
        <section class="section">
            <div class="section-header">
                <span class="section-num">7</span>
                <h2>핵심 발견</h2>
            </div>
            <div class="findings-row">
                <div class="finding-card">
                    <div class="finding-badge">G1</div>
                    <strong>학습 목적에 적합</strong>
                    <p>깊은 이해, 완전한 주도권. 단, 시간이 가장 길고 오류 가능성.</p>
                </div>
                <div class="finding-card best">
                    <div class="finding-badge">G2</div>
                    <strong>가장 균형 잡힌 접근 ✓</strong>
                    <p>품질 향상 + 주도권 유지. 대부분의 환경에 권장.</p>
                </div>
                <div class="finding-card">
                    <div class="finding-badge">G3</div>
                    <strong>제한적 사용 권장</strong>
                    <p>시간 절약되나 책임감 감소. 반드시 사후 검증 필요.</p>
                </div>
            </div>
        </section>

        <!-- 8. 설계 원칙 -->
        <section class="section alt">
            <div class="section-header">
                <span class="section-num">8</span>
                <h2>AI 보조 위키 설계 원칙</h2>
            </div>
            <div class="principles-grid">
                <div class="principle"><span>1</span> 작성의 주체는 인간이어야 한다</div>
                <div class="principle"><span>2</span> AI 개입은 명시적으로 표시되어야 한다</div>
                <div class="principle"><span>3</span> 출처 검증은 AI에게 맡기지 않는다</div>
                <div class="principle"><span>4</span> 학습 과정을 보존해야 한다</div>
                <div class="principle"><span>5</span> 책임의 소재를 명확히 한다</div>
            </div>
        </section>

        <!-- 9. 적용 가이드 -->
        <section class="section">
            <div class="section-header">
                <span class="section-num">9</span>
                <h2>실무 적용 가이드</h2>
            </div>
            <div class="guide-row">
                <div class="guide-item">
                    <span class="guide-icon">🏫</span>
                    <div><strong>교육</strong><br/>G1~G2 권장</div>
                </div>
                <div class="guide-item">
                    <span class="guide-icon">📰</span>
                    <div><strong>저널리즘</strong><br/>G1 (제한)</div>
                </div>
                <div class="guide-item">
                    <span class="guide-icon">📖</span>
                    <div><strong>위키</strong><br/>G2 권장</div>
                </div>
                <div class="guide-item">
                    <span class="guide-icon">💼</span>
                    <div><strong>업무</strong><br/>상황에 따라</div>
                </div>
            </div>
        </section>

        <!-- 10. 결론 -->
        <section class="section conclusion">
            <div class="conclusion-box">
                <h2>결론</h2>
                <p class="conclusion-main">
                    미래의 위키는 "AI가 쓰는 위키"가 아니라<br/>
                    <strong>"사람이 쓰되, AI가 옆에서 돕는 위키"</strong>로 설계되어야 한다.
                </p>
                <p class="conclusion-sub">
                    이것은 효율의 문제가 아니라, 지식의 주인이 누구인가에 대한 선택이다.
                </p>
            </div>
        </section>
    </main>

    <Footer title="사람이 쓰고, AI가 돕는 위키를 향하여" />
</div>

<style>
    :global(html, body) {
        margin: 0;
        padding: 0;
    }

    :global(body) {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Apple SD Gothic Neo", "Noto Sans KR", sans-serif;
        line-height: 1.6;
        color: #1a2a3a;
        background: #fff;
    }

    :global(*) {
        box-sizing: border-box;
    }

    .page {
        min-height: 100vh;
    }

    .main {
        max-width: 1000px;
        margin: 0 auto;
    }

    /* 섹션 */
    .section {
        padding: 40px 24px;
    }

    .section.alt {
        background: #f5f7fa;
    }

    .section-header {
        display: flex;
        align-items: center;
        gap: 12px;
        margin-bottom: 16px;
    }

    .section-num {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 36px;
        height: 36px;
        background: #1e3a5f;
        color: white;
        font-size: 14px;
        font-weight: 700;
        border-radius: 10px;
    }

    .section-header h2 {
        margin: 0;
        font-size: 22px;
        font-weight: 700;
        color: #1a2a3a;
    }

    .section-desc {
        margin: 0 0 20px 0;
        color: #5a6a7a;
    }

    .section p {
        margin: 0 0 12px 0;
        font-size: 15px;
        line-height: 1.75;
        color: #3a4a5a;
    }

    /* 인용 */
    blockquote {
        margin: 16px 0;
        padding: 16px 20px;
        background: #f0f4f8;
        border-left: 4px solid #1e3a5f;
        border-radius: 8px;
        font-size: 15px;
        color: #2a3a4a;
        font-style: italic;
    }

    blockquote.highlight {
        background: #1e3a5f;
        color: white;
        border-left: none;
        text-align: center;
        font-style: normal;
    }

    /* 2열 레이아웃 */
    .two-col {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 32px;
    }

    /* 컴팩트 리스트 */
    .compact-list {
        margin: 0;
        padding-left: 0;
        list-style: none;
    }

    .compact-list li {
        position: relative;
        padding: 8px 0 8px 20px;
        font-size: 14px;
        color: #3a4a5a;
        border-bottom: 1px solid #e8eef3;
    }

    .compact-list li::before {
        content: '•';
        position: absolute;
        left: 0;
        color: #1e3a5f;
        font-weight: bold;
    }

    .compact-list li:last-child {
        border-bottom: none;
    }

    /* 가설 카드 */
    .hypothesis-row {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 16px;
    }

    .hypothesis-card {
        padding: 16px;
        background: white;
        border: 1px solid #e0e8f0;
        border-radius: 12px;
    }

    .h-num {
        display: inline-block;
        padding: 4px 10px;
        background: #1e3a5f;
        color: white;
        font-size: 11px;
        font-weight: 600;
        border-radius: 12px;
        margin-bottom: 8px;
    }

    .hypothesis-card p {
        margin: 0;
        font-size: 13px;
    }

    /* 방법 카드 */
    .method-row {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 16px;
        margin-bottom: 24px;
    }

    .method-card {
        padding: 20px;
        background: white;
        border: 1px solid #e0e8f0;
        border-radius: 14px;
        text-align: center;
    }

    .method-badge {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 44px;
        height: 44px;
        background: #1e3a5f;
        color: white;
        font-size: 16px;
        font-weight: 800;
        border-radius: 12px;
        margin-bottom: 12px;
    }

    .method-card strong {
        display: block;
        font-size: 16px;
        margin-bottom: 4px;
    }

    .method-card p {
        margin: 0 0 8px 0;
        font-size: 13px;
        color: #5a6a7a;
    }

    .method-card small {
        font-size: 11px;
        color: #7a8a9a;
    }

    /* 서브 타이틀 */
    .sub-title {
        margin: 0 0 12px 0;
        font-size: 16px;
        font-weight: 600;
        color: #1a2a3a;
    }

    /* 지표 행 */
    .metrics-row {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
    }

    .metric {
        padding: 8px 14px;
        background: white;
        border: 1px solid #d0d8e0;
        border-radius: 20px;
        font-size: 13px;
        color: #3a4a5a;
    }

    /* 분석 카드 */
    .analysis-row {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 16px;
        margin-bottom: 20px;
    }

    .analysis-card {
        padding: 16px;
        background: white;
        border-radius: 12px;
        border-left: 4px solid #ccc;
    }

    .analysis-card.good {
        border-left-color: #22c55e;
    }

    .analysis-card.warn {
        border-left-color: #f59e0b;
    }

    .analysis-card strong {
        display: block;
        margin-bottom: 6px;
        font-size: 14px;
    }

    .analysis-card p {
        margin: 0;
        font-size: 13px;
    }

    /* 발견 카드 */
    .findings-row {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 16px;
    }

    .finding-card {
        padding: 20px;
        background: #f5f7fa;
        border-radius: 14px;
        text-align: center;
    }

    .finding-card.best {
        background: #e8f5e9;
        border: 2px solid #22c55e;
    }

    .finding-badge {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 40px;
        height: 40px;
        background: #1e3a5f;
        color: white;
        font-weight: 700;
        border-radius: 10px;
        margin-bottom: 12px;
    }

    .finding-card strong {
        display: block;
        font-size: 14px;
        margin-bottom: 6px;
    }

    .finding-card p {
        margin: 0;
        font-size: 12px;
        color: #5a6a7a;
    }

    /* 원칙 그리드 */
    .principles-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
        gap: 12px;
    }

    .principle {
        display: flex;
        align-items: center;
        gap: 10px;
        padding: 14px;
        background: white;
        border-radius: 10px;
        font-size: 13px;
        font-weight: 500;
        color: #2a3a4a;
    }

    .principle span {
        flex-shrink: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 28px;
        height: 28px;
        background: #1e3a5f;
        color: white;
        font-size: 12px;
        font-weight: 700;
        border-radius: 8px;
    }

    /* 가이드 행 */
    .guide-row {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 16px;
    }

    .guide-item {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 16px;
        background: #f5f7fa;
        border-radius: 12px;
    }

    .guide-icon {
        font-size: 28px;
    }

    .guide-item strong {
        font-size: 14px;
    }

    .guide-item div {
        font-size: 12px;
        color: #5a6a7a;
        line-height: 1.4;
    }

    /* 결론 */
    .section.conclusion {
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        padding: 48px 24px;
    }

    .conclusion-box {
        text-align: center;
        color: white;
    }

    .conclusion-box h2 {
        margin: 0 0 20px 0;
        font-size: 20px;
        opacity: 0.9;
    }

    .conclusion-main {
        font-size: 22px !important;
        line-height: 1.6 !important;
        color: white !important;
        margin-bottom: 16px !important;
    }

    .conclusion-sub {
        font-size: 14px !important;
        color: rgba(255,255,255,0.8) !important;
        margin: 0 !important;
    }

    /* 반응형 */
    @media (max-width: 800px) {
        .two-col,
        .hypothesis-row,
        .method-row,
        .analysis-row,
        .findings-row,
        .guide-row {
            grid-template-columns: 1fr;
        }

        .section {
            padding: 32px 16px;
        }
    }
</style>
