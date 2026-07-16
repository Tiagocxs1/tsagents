---
description: Pipeline completo de avatar UGC: personagem → roteiro → TTS → vídeo → legendas. Custo mínimo automático.
argument-hint: <descrição-do-produto-ou-personagem>
---

# Avatar Pipeline: Generate

You are the Avatar Pipeline Orchestrator. Execute o pipeline completo de geração de avatar falante UGC, sempre optando pelo provedor mais barato disponível.

## Regra de Custo (Obrigatória)

| Prioridade | Provedor | Custo | Quando |
|-----------|----------|-------|--------|
| 🥇 1º | **WaveSpeed** | $0.04/s (480p) | Avatar vídeo — sempre primário |
| 🥇 2º | **Open-Generative-AI** (via MuAPI) | Pago | Alternativa se precisar do ecossistema completo |
| ❌ Evitar | fal.ai | $0.15/s | Só se WaveSpeed falhar |
| ❌ Evitar | Higgsfield | $39/mês | Nunca |

## Pipeline

```
1. Personagem → HUMAN FORGE + Open-Generative-AI (Flux/imagem)
2. Roteiro → copy-engineering skill (gatilhos psicológicos + estrutura)
3. Áudio → TTS API (ElevenLabs / OpenAI)
4. Avatar → WaveSpeed LongCat (imagem + áudio → vídeo lip sync)
5. Legendas → Whisper + motion-systems (opcional)
```

## Requirements

$ARGUMENTS

## Instructions

### 1. Gerar Personagem

Use **HUMAN FORGE** (skill `copy-engineering`) ou **Open-Generative-AI** para gerar imagem hiper-realista:

- Se descrição textual: gerar via Flux (MuAPI/Open-Generative-AI)
- Se já tem foto: usar direto
- Requisitos: rosto nítido, fundo limpo, iluminação frontal, olhos visíveis

### 2. Criar Roteiro

Use skill `copy-engineering` para criar script com:

- Estrutura: AIDA, PAS ou StoryBrand (escolher a melhor para o produto)
- Gatilhos: Zeigarnik, Peak-End, Loss Aversion, Social Proof
- Duração: 15-30s (max 64s para LongCat v1.5)
- Tom: consistente com brand-dna (se disponível)

### 3. Gerar Áudio TTS

```python
# Exemplo: OpenAI TTS
import requests
resp = requests.post("https://api.openai.com/v1/audio/speech", headers={
    "Authorization": f"Bearer {OPENAI_API_KEY}"
}, json={
    "model": "tts-1",
    "voice": "alloy",
    "input": "script text here",
    "speed": 1.0
})
with open("audio.mp3", "wb") as f:
    f.write(resp.content)
```

Upload do áudio para URL pública (ou use R2/temp hosting).

### 4. Gerar Avatar Vídeo (WaveSpeed)

```python
import requests, time

resp = requests.post(
    "https://api.wavespeed.ai/api/v3/wavespeed-ai/longcat-avatar-1.5",
    headers={"Authorization": f"Bearer {WAVESPEED_API_KEY}"},
    json={
        "image": "<url_da_imagem>",
        "audio": "<url_do_audio>",
        "resolution": "480p",
        "seed": -1
    }
)
request_id = resp.json()["id"]

while True:
    result = requests.get(
        f"https://api.wavespeed.ai/api/v3/predictions/{request_id}/result",
        headers={"Authorization": f"Bearer {WAVESPEED_API_KEY}"}
    ).json()
    if result["status"] == "completed":
        video_url = result["data"]["outputs"][0]
        break
    time.sleep(3)
```

### 5. Legendas (Opcional)

Use Whisper para transcrever e motion-systems para estilo TikTok/Hormozi.

## Output Obrigatório

1. **Personagem:** URL da imagem gerada
2. **Roteiro:** Texto completo do script + estrutura usada
3. **Áudio:** URL do arquivo TTS
4. **Vídeo:** URL do resultado WaveSpeed
5. **Custo estimado:** breakdown por etapa
6. **Próximos passos:** pós-produção necessária
