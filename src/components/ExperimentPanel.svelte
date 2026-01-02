<script>
    import { onMount } from 'svelte';

    let apiKey = '';
    let topic = '';
    let selectedGroup = 'G1';
    let userText = '';
    let result = '';
    let loading = false;
    let error = '';
    let startTime = null;
    let elapsedTime = null;
    let step = 1; // 1: 주제 선택, 2: 작성, 3: 결과

    const groups = [
        { id: 'G1', name: 'AI 없음', desc: '사용자가 직접 작성' },
        { id: 'G2', name: 'AI 보조', desc: '맞춤법, 문장 다듬기, 출처 제안' },
        { id: 'G3', name: 'AI 초안', desc: 'AI가 초안 생성, 사용자 수정' }
    ];

    const sampleTopics = [
        '인공지능의 역사',
        '기후 변화의 원인',
        '한국 전통 음식',
        '태양계 행성들'
    ];

    onMount(() => {
        // 환경 변수에서 API 키 가져오기
        apiKey = process.env.OPENAI_API_KEY;
        console.log('apiKey', apiKey);
    });

    function startExperiment() {
        if (!topic.trim()) {
            error = '주제를 입력해주세요.';
            return;
        }
        error = '';
        step = 2;
        startTime = Date.now();

        if (selectedGroup === 'G3') {
            generateDraft();
        }
    }

    async function generateDraft() {
        if (!apiKey) {
            error = 'API 키가 설정되지 않았습니다.';
            return;
        }

        loading = true;
        try {
            const response = await fetch('https://api.openai.com/v1/chat/completions', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': `Bearer ${apiKey}`
                },
                body: JSON.stringify({
                    model: 'gpt-3.5-turbo',
                    messages: [
                        { 
                            role: 'system', 
                            content: '당신은 위키 백과 스타일의 문서 초안을 작성하는 전문가입니다. 객관적이고 중립적인 톤으로, 정확한 정보를 바탕으로 2-3 문단 정도의 간결한 초안을 작성해주세요.' 
                        },
                        { 
                            role: 'user', 
                            content: `"${topic}"에 대한 위키 스타일 문서 초안을 작성해주세요. 주요 내용을 포함하되, 간결하게 작성해주세요.` 
                        }
                    ],
                    temperature: 0.7,
                    max_tokens: 800
                })
            });

            if (!response.ok) {
                throw new Error('API 요청 실패');
            }

            const data = await response.json();
            userText = data.choices[0].message.content;
        } catch (err) {
            error = 'AI 초안 생성에 실패했습니다: ' + err.message;
        } finally {
            loading = false;
        }
    }

    async function applyAIAssist() {
        console.log('applyAIAssist', apiKey, userText);
        if (!apiKey || !userText.trim()) return;
        
        loading = true;
        error = '';
        try {
            const response = await fetch('https://api.openai.com/v1/chat/completions', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': `Bearer ${apiKey}`
                },
                body: JSON.stringify({
                    model: 'gpt-3.5-turbo',
                    messages: [
                        { 
                            role: 'system', 
                            content: '당신은 위키 문서를 다듬는 편집 보조 도구입니다. 사용자의 텍스트를 다음과 같이 개선해주세요: 1) 맞춤법과 문법 교정 2) 문장을 더 명확하게 다듬기 3) 관련 출처나 참고자료 제안. 원문의 의미는 유지하면서 품질만 향상시켜주세요.' 
                        },
                        { 
                            role: 'user', 
                            content: `다음 텍스트를 다듬고 출처를 제안해주세요:\n\n${userText}` 
                        }
                    ],
                    temperature: 0.5,
                    max_tokens: 1000
                })
            });

            if (!response.ok) {
                throw new Error('API 요청 실패');
            }

            const data = await response.json();
            userText = data.choices[0].message.content;
        } catch (err) {
            error = 'AI 보조 적용 실패: ' + err.message;
        } finally {
            loading = false;
        }
    }

    function finishExperiment() {
        elapsedTime = Math.round((Date.now() - startTime) / 1000);
        result = userText;
        step = 3;
    }

    function resetExperiment() {
        step = 1;
        topic = '';
        userText = '';
        result = '';
        error = '';
        elapsedTime = null;
    }
</script>

<div class="experiment-panel">
    <div class="experiment-header">
        <h3 class="experiment-title">🧪 실험 체험하기</h3>
        <p class="experiment-desc">직접 세 가지 그룹의 차이를 체험해보세요</p>
    </div>

    {#if step === 1}
        <div class="step-content">
            <div class="group-select">
                <label class="group-label">실험 그룹 선택</label>
                <div class="group-options">
                    {#each groups as group}
                        <label class="group-option" class:selected={selectedGroup === group.id}>
                            <input type="radio" name="group" value={group.id} bind:group={selectedGroup} />
                            <span class="group-badge">{group.id}</span>
                            <span class="group-info">
                                <strong>{group.name}</strong>
                                <small>{group.desc}</small>
                            </span>
                        </label>
                    {/each}
                </div>
            </div>

            <div class="topic-input">
                <label class="topic-label" for="topic">작성할 주제</label>
                <input 
                    id="topic"
                    type="text" 
                    placeholder="예: 인공지능의 역사" 
                    bind:value={topic}
                    class="topic-field"
                />
                <div class="sample-topics">
                    {#each sampleTopics as sample}
                        <button class="sample-btn" on:click={() => topic = sample}>
                            {sample}
                        </button>
                    {/each}
                </div>
            </div>

            {#if error}
                <div class="error-msg">{error}</div>
            {/if}

            <button class="start-btn" on:click={startExperiment}>
                실험 시작하기
            </button>
        </div>
    {:else if step === 2}
        <div class="step-content">
            <div class="writing-header">
                <span class="current-group">{groups.find(g => g.id === selectedGroup)?.name}</span>
                <span class="current-topic">주제: {topic}</span>
            </div>

            <div class="editor-area">
                <label class="editor-label" for="editor">
                    {#if selectedGroup === 'G3'}
                        AI가 생성한 초안을 수정하세요
                    {:else}
                        위키 문서를 작성하세요
                    {/if}
                </label>
                <textarea 
                    id="editor"
                    class="editor"
                    bind:value={userText}
                    placeholder={loading ? 'AI가 초안을 생성하는 중...' : '여기에 문서를 작성하세요...'}
                    disabled={loading}
                    rows="10"
                ></textarea>

                {#if selectedGroup === 'G2' && userText.trim()}
                    <button class="assist-btn" on:click={applyAIAssist} disabled={loading}>
                        {loading ? '처리 중...' : '✨ AI 보조 적용 (다듬기/출처 제안)'}
                    </button>
                {/if}
            </div>

            {#if error}
                <div class="error-msg">{error}</div>
            {/if}

            <div class="action-row">
                <button class="back-btn" on:click={resetExperiment}>
                    처음으로
                </button>
                <button class="finish-btn" on:click={finishExperiment} disabled={!userText.trim()}>
                    작성 완료
                </button>
            </div>
        </div>
    {:else if step === 3}
        <div class="step-content">
            <div class="result-header">
                <h4>실험 결과</h4>
                <div class="result-stats">
                    <span class="stat-item">
                        <strong>그룹:</strong> {selectedGroup} ({groups.find(g => g.id === selectedGroup)?.name})
                    </span>
                    <span class="stat-item">
                        <strong>소요 시간:</strong> {elapsedTime}초
                    </span>
                    <span class="stat-item">
                        <strong>글자 수:</strong> {result.length}자
                    </span>
                </div>
            </div>

            <div class="result-content">
                <h5>작성된 문서</h5>
                <div class="result-text">{result}</div>
            </div>

            <div class="result-questions">
                <p><strong>스스로 생각해보세요:</strong></p>
                <ul>
                    <li>이 문서를 "내가 썼다"고 느껴지나요?</li>
                    <li>문서 내용을 잘 이해하고 있나요?</li>
                    <li>다른 그룹으로 다시 실험해보세요!</li>
                </ul>
            </div>

            <button class="retry-btn" on:click={resetExperiment}>
                다시 실험하기
            </button>
        </div>
    {/if}
</div>

<style>
    .experiment-panel {
        background: white;
        border-radius: 24px;
        padding: 36px;
        box-shadow: 0 8px 40px rgba(30,58,95,0.12);
        border: 2px solid #2d5a87;
    }

    .experiment-header {
        text-align: center;
        margin-bottom: 32px;
    }

    .experiment-title {
        margin: 0 0 8px 0;
        font-size: 26px;
        font-weight: 700;
        color: #1a2a3a;
    }

    .experiment-desc {
        margin: 0;
        color: #5a6a7a;
        font-size: 15px;
    }

    .step-content {
        display: flex;
        flex-direction: column;
        gap: 24px;
    }

    .group-label,
    .topic-label,
    .editor-label {
        display: block;
        font-size: 14px;
        font-weight: 600;
        color: #3a4a5a;
        margin-bottom: 10px;
    }

    .group-options {
        display: flex;
        flex-direction: column;
        gap: 12px;
    }

    .group-option {
        display: flex;
        align-items: center;
        gap: 14px;
        padding: 16px 20px;
        background: #f8fafc;
        border: 2px solid #e8eef3;
        border-radius: 14px;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    .group-option:hover {
        border-color: #2d5a87;
        background: #f0f6fc;
    }

    .group-option.selected {
        border-color: #2d5a87;
        background: #e8f4fd;
    }

    .group-option input {
        display: none;
    }

    .group-badge {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 44px;
        height: 44px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        font-size: 16px;
        font-weight: 800;
        border-radius: 12px;
    }

    .group-info {
        display: flex;
        flex-direction: column;
        gap: 2px;
    }

    .group-info strong {
        font-size: 16px;
        color: #1a2a3a;
    }

    .group-info small {
        font-size: 13px;
        color: #6a7a8a;
    }

    .topic-field {
        width: 100%;
        padding: 14px 18px;
        font-size: 16px;
        border: 2px solid #e8eef3;
        border-radius: 12px;
        background: #f8fafc;
        transition: border-color 0.2s ease;
        box-sizing: border-box;
    }

    .topic-field:focus {
        outline: none;
        border-color: #2d5a87;
        background: white;
    }

    .sample-topics {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        margin-top: 12px;
    }

    .sample-btn {
        padding: 8px 14px;
        font-size: 13px;
        background: #f0f4f8;
        border: 1px solid #e0e8f0;
        border-radius: 20px;
        cursor: pointer;
        transition: all 0.2s ease;
        color: #4a5a6a;
    }

    .sample-btn:hover {
        background: #e8f4fd;
        border-color: #2d5a87;
        color: #2d5a87;
    }

    .error-msg {
        padding: 14px 18px;
        background: #fef2f2;
        border: 1px solid #fecaca;
        border-radius: 10px;
        color: #dc2626;
        font-size: 14px;
    }

    .start-btn,
    .finish-btn,
    .retry-btn {
        padding: 16px 32px;
        font-size: 16px;
        font-weight: 600;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        border: none;
        border-radius: 12px;
        cursor: pointer;
        transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .start-btn:hover,
    .finish-btn:hover,
    .retry-btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 20px rgba(30,58,95,0.3);
    }

    .start-btn:disabled,
    .finish-btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
        transform: none;
    }

    .writing-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 14px 20px;
        background: #f0f4f8;
        border-radius: 12px;
    }

    .current-group {
        padding: 6px 14px;
        background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 100%);
        color: white;
        font-size: 13px;
        font-weight: 600;
        border-radius: 20px;
    }

    .current-topic {
        font-size: 14px;
        color: #4a5a6a;
    }

    .editor {
        width: 100%;
        padding: 18px;
        font-size: 15px;
        line-height: 1.7;
        border: 2px solid #e8eef3;
        border-radius: 14px;
        background: #fafbfc;
        resize: vertical;
        min-height: 200px;
        font-family: inherit;
        box-sizing: border-box;
    }

    .editor:focus {
        outline: none;
        border-color: #2d5a87;
        background: white;
    }

    .editor:disabled {
        opacity: 0.7;
    }

    .assist-btn {
        padding: 12px 20px;
        font-size: 14px;
        font-weight: 600;
        background: linear-gradient(135deg, #f0f4f8 0%, #e8f4fd 100%);
        color: #2d5a87;
        border: 2px solid #2d5a87;
        border-radius: 10px;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    .assist-btn:hover:not(:disabled) {
        background: #e8f4fd;
    }

    .assist-btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }

    .action-row {
        display: flex;
        justify-content: space-between;
        gap: 16px;
    }

    .back-btn {
        padding: 14px 28px;
        font-size: 15px;
        font-weight: 600;
        background: #f0f4f8;
        color: #4a5a6a;
        border: 1px solid #e0e8f0;
        border-radius: 10px;
        cursor: pointer;
        transition: background 0.2s ease;
    }

    .back-btn:hover {
        background: #e8eef4;
    }

    .result-header {
        padding: 20px;
        background: linear-gradient(135deg, #f0f4f8 0%, #e8f4fd 100%);
        border-radius: 14px;
    }

    .result-header h4 {
        margin: 0 0 12px 0;
        font-size: 18px;
        color: #1a2a3a;
    }

    .result-stats {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
    }

    .stat-item {
        font-size: 14px;
        color: #4a5a6a;
    }

    .stat-item strong {
        color: #2d5a87;
    }

    .result-content {
        padding: 20px;
        background: #fafbfc;
        border-radius: 14px;
        border: 1px solid #e8eef3;
    }

    .result-content h5 {
        margin: 0 0 12px 0;
        font-size: 15px;
        color: #3a4a5a;
    }

    .result-text {
        font-size: 15px;
        line-height: 1.8;
        color: #2a3a4a;
        white-space: pre-wrap;
    }

    .result-questions {
        padding: 20px;
        background: #fffbeb;
        border-radius: 14px;
        border: 1px solid #fde68a;
    }

    .result-questions p {
        margin: 0 0 12px 0;
        color: #92400e;
    }

    .result-questions ul {
        margin: 0;
        padding-left: 20px;
        color: #a16207;
    }

    .result-questions li {
        margin-bottom: 6px;
    }

    @media (max-width: 600px) {
        .experiment-panel {
            padding: 24px;
        }

        .writing-header {
            flex-direction: column;
            gap: 10px;
            align-items: flex-start;
        }

        .action-row {
            flex-direction: column;
        }

        .result-stats {
            flex-direction: column;
            gap: 8px;
        }
    }
</style>

