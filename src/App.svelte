<script>
    import Header from './components/Header.svelte';
    import Section from './components/Section.svelte';
    import InfoCard from './components/InfoCard.svelte';
    import MethodCard from './components/MethodCard.svelte';
    import QuoteBox from './components/QuoteBox.svelte';
    import HypothesisCard from './components/HypothesisCard.svelte';
    import MetricItem from './components/MetricItem.svelte';
    import ExperimentPanel from './components/ExperimentPanel.svelte';
    import Footer from './components/Footer.svelte';

    const hypotheses = [
        { number: "1", text: "AI 보조(편집·검증 지원)는 문서 정확성과 출처 품질을 향상시킨다." },
        { number: "2", text: "AI가 초안을 작성하는 경우, 작성 시간은 단축되지만 작성자의 주도권 인식과 학습 효과는 감소한다." },
        { number: "3", text: "AI 개입이 일정 수준을 넘으면, 문서 품질 향상 대비 부작용(책임 약화)이 더 커진다." }
    ];

    const methods = [
        {
            id: "G1",
            title: "AI 없음",
            description: "인간만으로 작성하는 통제 그룹",
            features: ["직접 자료 조사", "자유로운 구성", "온전한 저자 경험"]
        },
        {
            id: "G2",
            title: "AI 보조",
            description: "편집과 검증을 돕는 보조 도구",
            features: ["맞춤법 교정", "문장 다듬기", "출처 후보 제안"]
        },
        {
            id: "G3",
            title: "AI 초안 허용",
            description: "AI가 초안 생성, 인간이 수정",
            features: ["초안 자동 생성", "수정/보완 중심", "빠른 작성 가능"]
        }
    ];

    const metrics = [
        { icon: "🎯", title: "정확성", description: "사실 오류의 개수" },
        { icon: "📚", title: "출처 품질", description: "출처 수와 신뢰도" },
        { icon: "⏱️", title: "작성 효율", description: "문서 완성까지 걸린 시간" },
        { icon: "✋", title: "주도권 인식", description: '"이 문서는 내가 직접 썼다"에 대한 설문' },
        { icon: "🧠", title: "학습 효과", description: "작성 후 주제 이해도 평가(퀴즈)" }
    ];
</script>

<div class="page">
    <Header 
        badge="연구 보고서"
        title="AI 보조 위키에서의 경계 설계에 관한 후속 탐구"
        subtitle="'도움'과 '대신 작성'을 구분하는 실험적 분석"
    />

    <main class="main">
        <!-- 1. 연구 배경 -->
        <Section number="1" title="연구 배경">
            <p>
                최근 인공지능은 문서 작성과 정보 정리에 있어 인간의 능력을 빠르게 대체하고 있다. 
                특히 대규모 언어 모델은 위키 문서를 포함한 지식 텍스트를 짧은 시간 안에 생성할 수 있으며, 
                이는 정보 생산의 효율을 크게 높인다. 그러나 이러한 변화는 위키나 글 작성성의 본질적 성격에 대한 
                근본적인 질문을 제기한다.
            </p>

            <QuoteBox>
                <p>
                    위키나 글 작성은 단순한 정보 저장소가 아니라, 사람이 직접 쓰고 서로 검증하는 과정 자체를 통해 
                    신뢰를 형성해 온 지식 시스템이다.
                </p>
            </QuoteBox>

            <p>
                만약 AI가 문서를 대신 작성하는 역할을 맡게 된다면, 사용자는 더 이상 지식의 생산자나 
                검증자가 아니라 결과를 소비하는 존재로 전락할 가능성이 있다. 이는 책임의 주체를 
                불분명하게 만들고, 장기적으로는 위키의 신뢰 구조를 약화시킬 수 있다.
            </p>

            <p>
                따라서 본 연구는 <strong>"AI를 전면적으로 허용할 것인가"</strong>라는 이분법적 질문을 넘어서, 
                <strong>AI의 개입 수준을 어떻게 설계해야 위키의 핵심 가치를 유지할 수 있는가</strong>에 
                초점을 맞춘다. 특히 'AI 보조'와 'AI 대체'의 경계를 실험적으로 구분하는 것을 
                연구의 출발점으로 삼는다.
            </p>
        </Section>

        <!-- 2. 연구 목적 -->
        <Section number="2" title="연구 목적" accent>
            <div class="purpose-grid">
                <InfoCard icon="📊" title="품질 분석">
                    <p>AI의 개입 수준에 따라 문서 품질과 작성자 인식이 어떻게 변화하는지 분석한다.</p>
                </InfoCard>
                <InfoCard icon="🤝" title="관계 검증">
                    <p>사용자가 느끼는 주도권, 책임감, 학습 효과가 AI 개입 정도와 어떤 관계를 가지는지 검증한다.</p>
                </InfoCard>
                <InfoCard icon="💡" title="대안 제시">
                    <p>'AI 초안 작성'이 항상 효율적이라는 가정을 비판적으로 검토하고, 보조 중심 설계의 가능성을 제시한다.</p>
                </InfoCard>
            </div>
        </Section>

        <!-- 3. 연구 질문 -->
        <Section number="3" title="연구 질문">
            <p>본 연구는 다음의 연구 질문을 중심으로 진행된다.</p>
            <div class="questions-list">
                <div class="question-item">
                    <span class="question-num">Q1</span>
                    <p>AI의 개입 수준이 달라질 때 문서의 정확성과 출처 품질은 어떻게 변화하는가?</p>
                </div>
                <div class="question-item">
                    <span class="question-num">Q2</span>
                    <p>사용자는 어느 지점부터 "이 문서는 내가 쓴 것이 아니다"라고 인식하는가?</p>
                </div>
                <div class="question-item">
                    <span class="question-num">Q3</span>
                    <p>AI 보조가 학습 효과를 저해하는지, 혹은 오히려 강화하는지 확인할 수 있는가?</p>
                </div>
            </div>
        </Section>

        <!-- 4. 연구 가설 -->
        <Section number="4" title="연구 가설" accent>
            <p>본 탐구는 다음과 같은 가설을 설정한다.</p>
            <div class="hypotheses-list">
                {#each hypotheses as h}
                    <HypothesisCard number={h.number} text={h.text} />
                {/each}
            </div>
        </Section>

        <!-- 5. 연구 방법 -->
        <Section number="5" title="연구 방법">
            <h3 class="subsection-title">5.1 실험 설계</h3>
            <p>동일한 주제의 위키 문서를 세 개의 그룹이 작성한다.</p>
            
            <div class="methods-grid">
                {#each methods as method}
                    <MethodCard 
                        id={method.id}
                        title={method.title}
                        description={method.description}
                        features={method.features}
                    />
                {/each}
            </div>

            <InfoCard variant="highlight">
                <p><strong>통제 조건:</strong> 모든 그룹은 동일한 시간 제한과 동일한 참고 자료 접근 권한을 가진다.</p>
            </InfoCard>

            <h3 class="subsection-title">5.2 평가 지표</h3>
            <p>문서 결과물과 작성자 인식을 다음 기준으로 평가한다.</p>
            
            <div class="metrics-grid">
                {#each metrics as metric}
                    <MetricItem 
                        icon={metric.icon}
                        title={metric.title}
                        description={metric.description}
                    />
                {/each}
            </div>
        </Section>

        <!-- 실험 체험 섹션 -->
        <Section number="⚡" title="직접 체험해보기" accent>
            <p>연구에서 제시한 세 가지 그룹(G1, G2, G3)의 차이를 직접 체험해볼 수 있습니다.</p>
            <ExperimentPanel />
        </Section>

        <!-- 6. 분석 및 논의 -->
        <Section number="6" title="분석 및 논의">
            <p>
                본 실험은 단순히 "AI가 더 좋은 문서를 만드는가"를 묻지 않는다. 
                대신 다음과 같은 구조적 차이에 주목한다.
            </p>

            <div class="analysis-grid">
                <InfoCard title="G2 (보조 중심)" icon="✅">
                    <p>오류 감소와 출처 품질 개선에서 안정적인 성과를 보일 가능성이 높다.</p>
                </InfoCard>
                <InfoCard title="G3 (초안 허용)" icon="⚠️">
                    <p>작성 시간 단축이라는 명확한 장점을 가지지만, 작성자가 문서의 내용 구조를 충분히 이해하지 못한 채 수정에만 참여할 가능성이 있다.</p>
                </InfoCard>
            </div>

            <QuoteBox>
                <p>
                    효율만을 기준으로 보면 AI 초안 작성이 우월해 보일 수 있으나, 
                    위키의 장기적 관점에서는 <strong>사람의 이해 과정 자체가 중요한 가치</strong>임을 드러낸다.
                </p>
            </QuoteBox>
        </Section>

        <!-- 7. 결과 해석의 의미 -->
        <Section number="7" title="결과 해석의 의미" accent>
            <InfoCard variant="primary">
                <p style="font-size: 20px; line-height: 1.8; text-align: center;">
                    AI는 문서를 대신 써줄 때 가장 편리하지만,<br/>
                    <strong>위키를 건강하게 만들 때는 사람이 쓰도록 도울 때 가장 효과적이다.</strong>
                </p>
            </InfoCard>

            <p style="margin-top: 32px;">
                이는 AI 활용 여부의 문제가 아니라, <strong>설계 철학의 문제</strong>이다.
                AI를 "저자"로 둘 것인지, "도구"로 둘 것인지에 따라 위키의 성격은 완전히 달라진다.
            </p>
        </Section>

        <!-- 8. 한계 및 윤리적 고려 -->
        <Section number="8" title="한계 및 윤리적 고려">
            <div class="limitations-grid">
                <InfoCard icon="📏" title="연구 한계">
                    <p>본 연구는 비교적 소규모 실험을 전제로 하므로, 참여자 수와 주제 다양성에 한계가 있다. 또한 AI 모델의 성능 차이에 따라 결과가 달라질 가능성도 존재한다.</p>
                </InfoCard>
                <InfoCard icon="⚖️" title="윤리적 고려">
                    <p>AI 초안 작성이 실제 환경에서 사용될 경우 저작권, 책임 소재, 허위 정보 확산 문제를 동반할 수 있음을 인식해야 한다.</p>
                </InfoCard>
            </div>
        </Section>

        <!-- 9. 결론 -->
        <Section number="9" title="결론" accent>
            <p>
                본 연구는 AI와 위키의 관계를 기술 발전의 필연으로 받아들이기보다,
                <strong>"어떻게 설계할 것인가"</strong>라는 질문으로 전환한다.
            </p>

            <p>
                실험을 통해 <strong>AI 보조는 위키의 품질과 학습 효과를 강화</strong>할 수 있지만,
                <strong>AI 대체는 위키의 핵심 가치인 책임과 참여를 약화</strong>시킬 수 있음을 보여준다.
            </p>

            <h3 class="subsection-title">9.1 핵심 발견</h3>
            <div class="conclusion-findings">
                <InfoCard icon="📌" title="G1 (AI 없음) 그룹">
                    <p><strong>장점:</strong> 작성자가 문서의 모든 내용을 직접 조사하고 구성하므로, 주제에 대한 깊은 이해와 완전한 주도권을 확보한다.</p>
                    <p><strong>단점:</strong> 작성 시간이 가장 길고, 맞춤법이나 문장 구조의 오류가 발생할 수 있다.</p>
                    <p><strong>결론:</strong> 학습 목적이 강한 환경(교육, 연구)에 적합하다.</p>
                </InfoCard>
                <InfoCard icon="📌" title="G2 (AI 보조) 그룹">
                    <p><strong>장점:</strong> 작성자가 내용을 직접 구성하면서도, 맞춤법 교정과 출처 제안으로 문서 품질이 향상된다. 주도권과 학습 효과를 유지하면서 효율성이 개선된다.</p>
                    <p><strong>단점:</strong> AI 제안을 무비판적으로 수용할 경우, 작성자의 의도와 다른 방향으로 문서가 변형될 수 있다.</p>
                    <p><strong>결론:</strong> 가장 균형 잡힌 접근법으로, 대부분의 위키 환경에 권장된다.</p>
                </InfoCard>
                <InfoCard icon="📌" title="G3 (AI 초안) 그룹">
                    <p><strong>장점:</strong> 작성 시간이 가장 짧고, 문서의 기본 구조가 빠르게 완성된다.</p>
                    <p><strong>단점:</strong> 작성자가 "이 글은 내가 쓴 것"이라는 인식이 약화되며, 내용에 대한 이해도와 책임감이 감소한다. AI가 생성한 부정확한 정보를 그대로 유지할 위험이 있다.</p>
                    <p><strong>결론:</strong> 시간이 극히 제한된 상황에서만 제한적으로 사용하고, 반드시 사후 검증이 필요하다.</p>
                </InfoCard>
            </div>

            <h3 class="subsection-title">9.2 AI 보조 위키 설계 원칙</h3>
            <div class="principles-list">
                <div class="principle-item">
                    <span class="principle-num">1</span>
                    <div class="principle-content">
                        <strong>작성의 주체는 인간이어야 한다</strong>
                        <p>AI는 초안을 생성하는 "저자"가 아니라, 인간의 작성을 돕는 "도구"로 위치해야 한다. 문서의 구조, 논점, 주장은 반드시 인간이 결정한다.</p>
                    </div>
                </div>
                <div class="principle-item">
                    <span class="principle-num">2</span>
                    <div class="principle-content">
                        <strong>AI 개입은 명시적으로 표시되어야 한다</strong>
                        <p>AI가 수정하거나 제안한 부분은 시각적으로 구분되어야 한다. 독자는 어떤 내용이 인간의 판단이고 어떤 부분이 AI 제안인지 알 권리가 있다.</p>
                    </div>
                </div>
                <div class="principle-item">
                    <span class="principle-num">3</span>
                    <div class="principle-content">
                        <strong>출처 검증은 AI에게 맡기지 않는다</strong>
                        <p>AI는 출처 후보를 제안할 수 있지만, 해당 출처의 신뢰성과 적절성 판단은 인간이 수행한다. AI가 제시한 출처가 실제로 존재하는지, 내용이 정확한지 반드시 확인한다.</p>
                    </div>
                </div>
                <div class="principle-item">
                    <span class="principle-num">4</span>
                    <div class="principle-content">
                        <strong>학습 과정을 보존해야 한다</strong>
                        <p>위키 작성은 지식 생산 과정이자 학습 과정이다. AI가 이 과정을 대체하면 작성자의 학습 기회가 박탈된다. 특히 교육 환경에서는 G2(보조) 방식을 권장한다.</p>
                    </div>
                </div>
                <div class="principle-item">
                    <span class="principle-num">5</span>
                    <div class="principle-content">
                        <strong>책임의 소재를 명확히 한다</strong>
                        <p>문서에 오류가 있을 때 책임은 AI가 아닌 인간에게 있다. 따라서 인간이 검토하지 않은 AI 생성 콘텐츠는 게시되어서는 안 된다.</p>
                    </div>
                </div>
            </div>

            <h3 class="subsection-title">9.3 실무 적용 가이드</h3>
            <div class="guide-grid">
                <InfoCard icon="🏫" title="교육 환경">
                    <p><strong>권장:</strong> G1 또는 G2</p>
                    <p>학생이 직접 조사하고 작성하는 과정이 학습의 핵심이다. AI는 맞춤법 검사와 문장 다듬기 수준으로 제한한다.</p>
                </InfoCard>
                <InfoCard icon="📰" title="뉴스/저널리즘">
                    <p><strong>권장:</strong> G1 (AI 사용 제한)</p>
                    <p>팩트 체크와 취재의 책임이 명확해야 하므로, AI 초안 생성은 적절하지 않다. 문법 검사 정도만 허용한다.</p>
                </InfoCard>
                <InfoCard icon="📖" title="백과사전/위키">
                    <p><strong>권장:</strong> G2</p>
                    <p>다수의 편집자가 상호 검증하는 환경에서 AI 보조는 효율을 높인다. 단, 모든 AI 제안은 인간이 검토 후 반영한다.</p>
                </InfoCard>
                <InfoCard icon="💼" title="업무 문서">
                    <p><strong>권장:</strong> G2 또는 G3 (상황에 따라)</p>
                    <p>반복적인 형식 문서는 G3가 효율적일 수 있으나, 의사결정이 포함된 문서는 반드시 G2 이하로 제한한다.</p>
                </InfoCard>
            </div>

            <QuoteBox highlight>
                <p style="text-align: center; font-size: 20px;">
                    미래의 위키는<br/>
                    "AI가 쓰는 위키"가 아니라<br/>
                    <strong>"사람이 쓰되, AI가 옆에서 돕는 위키"</strong>로 설계되어야 한다.<br/><br/>
                    <span style="font-size: 16px; opacity: 0.9;">
                        이것은 효율의 문제가 아니라, 지식의 주인이 누구인가에 대한 선택이다.
                    </span>
                </p>
            </QuoteBox>
        </Section>
    </main>

    <Footer title="사람이 쓰고, AI가 돕는 위키를 향하여" />
</div>

<style>
    :global(html, body) {
        margin: 0;
        padding: 0;
        height: 100%;
    }

    :global(body) {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Apple SD Gothic Neo", "Noto Sans KR", sans-serif;
        line-height: 1.6;
        color: #1a2a3a;
        background: #fafbfc;
    }

    :global(*) {
        box-sizing: border-box;
    }

    .page {
        min-height: 100vh;
    }

    .main {
        width: 100%;
    }

    /* 목적 그리드 */
    .purpose-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 20px;
        margin-top: 24px;
    }

    /* 연구 질문 리스트 */
    .questions-list {
        display: flex;
        flex-direction: column;
        gap: 16px;
        margin-top: 24px;
    }

    .question-item {
        display: flex;
        align-items: flex-start;
        gap: 20px;
        padding: 24px;
        background: white;
        border-radius: 16px;
        border: 1px solid #e8eef3;
        box-shadow: 0 2px 12px rgba(0,0,0,0.04);
    }

    .question-num {
        flex-shrink: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 48px;
        height: 48px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        font-size: 16px;
        font-weight: 800;
        border-radius: 12px;
    }

    .question-item p {
        margin: 0;
        font-size: 17px;
        line-height: 1.7;
        color: #2a3a4a;
        padding-top: 8px;
    }

    /* 가설 리스트 */
    .hypotheses-list {
        display: flex;
        flex-direction: column;
        gap: 16px;
        margin-top: 24px;
    }

    /* 서브섹션 타이틀 */
    .subsection-title {
        margin: 40px 0 20px 0;
        font-size: 22px;
        font-weight: 700;
        color: #1a2a3a;
        padding-left: 16px;
        border-left: 4px solid #2d5a87;
    }

    /* 방법 그리드 */
    .methods-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 24px;
        margin: 24px 0 32px;
    }

    /* 지표 그리드 */
    .metrics-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 16px;
        margin-top: 24px;
    }

    /* 분석 그리드 */
    .analysis-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 20px;
        margin: 24px 0;
    }

    /* 한계 그리드 */
    .limitations-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 20px;
    }

    /* 결론 발견 그리드 */
    .conclusion-findings {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 20px;
        margin-top: 24px;
    }

    /* 원칙 리스트 */
    .principles-list {
        display: flex;
        flex-direction: column;
        gap: 16px;
        margin-top: 24px;
    }

    .principle-item {
        display: flex;
        align-items: flex-start;
        gap: 20px;
        padding: 24px;
        background: white;
        border-radius: 16px;
        border: 1px solid #e8eef3;
        box-shadow: 0 2px 12px rgba(0,0,0,0.04);
        transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .principle-item:hover {
        transform: translateX(8px);
        box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    }

    .principle-num {
        flex-shrink: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 40px;
        height: 40px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        font-size: 18px;
        font-weight: 800;
        border-radius: 12px;
    }

    .principle-content {
        flex: 1;
    }

    .principle-content strong {
        display: block;
        font-size: 17px;
        color: #1a2a3a;
        margin-bottom: 8px;
    }

    .principle-content p {
        margin: 0;
        font-size: 15px;
        line-height: 1.7;
        color: #4a5a6a;
    }

    /* 가이드 그리드 */
    .guide-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 20px;
        margin-top: 24px;
    }

    @media (max-width: 768px) {
        .purpose-grid,
        .methods-grid,
        .metrics-grid,
        .analysis-grid,
        .limitations-grid,
        .conclusion-findings,
        .guide-grid {
            grid-template-columns: 1fr;
        }
    }
</style>
