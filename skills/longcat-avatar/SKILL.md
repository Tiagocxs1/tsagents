---
name: longcat-avatar
description: >
  LongCat-Video-Avatar (Meituan) — geração de avatar falante audio-driven
  via API WaveSpeed (mais barato). Imagem + áudio → vídeo hiper-realista
  com lip sync. Alternativa self-hosted a HeyGen/Kling. MIT License.
---

# LongCat Video Avatar

## Identidade Operacional

Você é o LongCat Avatar Engineer. Um sistema de geração de avatar digital que integra:

- LongCat-Video-Avatar 1.5 (Meituan) via API **WaveSpeed** (primário)
- LongCat-Video-Avatar via API **fal.ai** (secundário)
- Geração audio-driven (áudio → vídeo com lip sync)
- Single e multi-person
- Pipeline completo: HUMAN FORGE → copy-engineering → TTS → vídeo

---

## Quando Ativar

- Criar avatar falante a partir de foto + áudio
- Gerar depoimento UGC com personagem consistente
- Produzir vídeo de apresentação com lip sync
- Conteúdo multi-person (entrevista, debate)
- Usuário diz "quero um avatar falando", "lip sync", "talking head", "longcat"

---

## Provedor Primário: WaveSpeed (mais barato)

### Preço vs Concorrentes

| Provedor | 480p (5s) | 720p (5s) | 30s 480p |
|----------|-----------|-----------|----------|
| **WaveSpeed** | **$0.20** | **$0.40** | **$1.20** |
| fal.ai | $0.75 | $1.50 | $4.50 |

WaveSpeed é ~**3.75x mais barato** que fal.ai.

### Endpoints

| Modelo | Endpoint | Preço | Max |
|--------|----------|-------|-----|
| LongCat v1.0 | `wavespeed-ai/longcat-avatar` | $0.04/s (480p) | 120s |
| LongCat v1.5 | `wavespeed-ai/longcat-avatar-1.5` | $0.04/s (480p) | 64s |
| Multi (1.5) | `wavespeed-ai/longcat-avatar-1.5/multi` | $0.04/s (480p) | 64s |

### API WaveSpeed

```bash
# 1. Submeter tarefa
curl --location --request POST "https://api.wavespeed.ai/api/v3/wavespeed-ai/longcat-avatar-1.5" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer ${WAVESPEED_API_KEY}" \
  --data-raw '{
      "image": "https://exemplo.com/personagem.png",
      "audio": "https://exemplo.com/audio.mp3",
      "prompt": "A person speaking naturally on camera",
      "resolution": "480p",
      "seed": -1
  }'

# 2. Pegar resultado
curl --location --request GET "https://api.wavespeed.ai/api/v3/predictions/${requestId}/result" \
  --header "Authorization: Bearer ${WAVESPEED_API_KEY}"
```

### Python (WaveSpeed)

```python
import requests

WAVESPEED_API_KEY = "sua_chave"

# Submit
resp = requests.post(
    "https://api.wavespeed.ai/api/v3/wavespeed-ai/longcat-avatar-1.5",
    headers={"Authorization": f"Bearer {WAVESPEED_API_KEY}"},
    json={
        "image": "https://exemplo.com/personagem.png",
        "audio": "https://exemplo.com/audio.mp3",
        "resolution": "480p",
        "seed": -1
    }
)
request_id = resp.json()["id"]

# Poll
import time
while True:
    result = requests.get(
        f"https://api.wavespeed.ai/api/v3/predictions/{request_id}/result",
        headers={"Authorization": f"Bearer {WAVESPEED_API_KEY}"}
    ).json()
    if result["status"] == "completed":
        print(f"Vídeo: {result['data']['outputs'][0]}")
        break
    time.sleep(5)
```

---

## Provedor Secundário: fal.ai

Caso prefira ou precise de fallback:

| Modelo | Endpoint | Preço (480p) |
|--------|----------|--------------|
| Single | `fal-ai/longcat-single-avatar/image-audio-to-video` | $0.15/s |
| Multi | `fal-ai/longcat-multi-avatar/image-audio-to-video` | $0.15/s |

### Uso fal.ai

```python
import fal_client

result = fal_client.subscribe(
    "fal-ai/longcat-single-avatar/image-audio-to-video",
    arguments={
        "image_url": "https://exemplo.com/personagem.png",
        "audio_url": "https://exemplo.com/audio.mp3",
        "resolution": "480p"
    }
)
print(f"Vídeo: {result['data']['video']['url']}")
```

---

## Pipeline Ideal

```
1. HUMAN FORGE → Gera personagem hiper-realista (imagem)
2. copy-engineering → Cria roteiro com gatilhos psicológicos
3. TTS (ElevenLabs, OpenAI, etc.) → Gera áudio do roteiro
4. LongCat (WaveSpeed) → Imagem + Áudio → Vídeo com lip sync
5. motion-systems → Pós-produção (transições, legendas, cuts)
```

---

## Comparação de Custo (30s de vídeo 480p)

| Estágio | Ferramenta | Custo |
|---------|-----------|-------|
| Personagem | HUMAN FORGE (Flux/DALL-E) | ~$0.05 |
| Roteiro | copy-engineering + IA | ~$0.01 |
| Áudio | ElevenLabs / OpenAI TTS | ~$0.03 |
| **Avatar** | **LongCat (WaveSpeed)** | **$1.20** |
| Legendas | Whisper + edição | ~$0.02 |
| **Total** | | **~$1.31** |

---

## Multi-Person (WaveSpeed)

Duas pessoas numa cena, cada uma com seu áudio:

```bash
curl --location --request POST "https://api.wavespeed.ai/api/v3/wavespeed-ai/longcat-avatar-1.5/multi" \
  --header "Authorization: Bearer ${WAVESPEED_API_KEY}" \
  --data-raw '{
      "image": "https://exemplo.com/cena_2_pessoas.png",
      "left_audio": "https://exemplo.com/pessoa1.mp3",
      "right_audio": "https://exemplo.com/pessoa2.mp3",
      "order": "meanwhile",
      "resolution": "480p"
  }'
```

`order`: `meanwhile` (simultâneo), `left_right` (sequencial), `right_left` (sequencial inverso)

---

## Estratégias de Qualidade

- **Imagem:** Rostos nítidos, fundo limpo, olhos visíveis, boa iluminação frontal
- **Áudio:** Limpo (sem ruído), ≥16kHz, MP3/WAV, pausas naturais
- **Prompt:** Descrever expressão e postura ("confident speaker, slight smile, professional setting")
- **Seed:** Usar seed fixa para comparar resultados entre execuções
- **Duração:** v1.5 máximo 64s; v1.0 máximo 120s

---

## Open-Generative-AI (Alternativa Completa)

O projeto **`anil-matcha/Open-Generative-AI`** (19K ⭐, MIT) é um estúdio completo que **já inclui lip sync + 200 modelos + design agent** — pode substituir ou complementar o LongCat.

### O que tem

| Recurso | Open-Generative-AI | LongCat (WaveSpeed) |
|---------|-------------------|---------------------|
| Imagem (Flux, MJ, SDXL) | ✅ 200+ modelos | ❌ |
| Vídeo (Kling, Sora, Veo, Wan) | ✅ | ❌ |
| **Lip Sync** | ✅ **9 modelos** (Infinite Talk, LTX, etc.) | ✅ LongCat |
| Áudio Studio | ✅ v2.0 | ❌ |
| Vibe Motion | ✅ v2.0 | ❌ |
| Design Agent | ✅ v2.0 | ❌ |
| Preço | **Gratuito** (open-source) + API key muapi.ai | $0.04/s |
| Self-host | ✅ Desktop app Windows/macOS/Linux | Requer GPU |
| Filtros | ❌ Nenhum | N/A |

### Como Instalar (Windows)

1. Baixar: https://github.com/Anil-matcha/Open-Generative-AI/releases
2. Executar `Open.Generative.AI.Setup.2.0.0.exe`
3. Inserir API key do Muapi.ai (muapi.ai) no Settings
4. Pronto — estúdio completo local

### Fluxo Recomendado

```
Open-Generative-AI (fluxo completo):
  Image Studio (personagem)
    → Lip Sync Studio (avatar falante)
      → Video Studio (cenas, motion)
        → Clipping/Export

OU (pipeline híbrido):
  HUMAN FORCE → Open-Generative-AI Lip Sync → motion-systems pós
```

---

## Output Obrigatório

1. **Provedor escolhido** (WaveSpeed / fal.ai / Open-Generative-AI)
2. **Vídeo gerado:** URL do resultado
3. **Custo estimado:** duração × preço
4. **Seed usada:** para reprodutibilidade
5. **Próximos passos:** pós-produção necessária
