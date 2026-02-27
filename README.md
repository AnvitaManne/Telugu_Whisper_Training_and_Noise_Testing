# Telugu Whisper Training and Testing
This repository documents the fine-tuning of OpenAI's **Whisper-Small** and evaluating its performance against a custom-curated corpus of noise-augmented speech.

## Technical Methodology

### Hardware and Environment

* **Platform:** RunPod.
* **GPU:** NVIDIA A40 (48 GB VRAM).
* **Framework:** PyTorch + Hugging Face Transformers.

### Training Configuration

The model was fine-tuned to optimize for phonetic accuracy in Telugu:

* **Optimizer:** RMSProp.
* **Learning Rate**: $1e-5$.
* **Batch Size**: 16.
* **Epochs**: 20.

## Noise-Resilience Evaluation

To test real-world robustness, the model was benchmarked against the **Telugu-Noisy-Data** corpus, which consists of speech from Mozilla Common Voice, IndicTTS, and OpenSLR augmented with **ESC-50** environmental noise (rain, wind, urban sounds).

### Results on testing against noisy data

| Metric | Global Result |
| --- | --- |
| **Total Files Processed** | 7,368 |
| **Global Corpus WER** | **13.97%** |
| **Global Corpus CER** | **3.54%** |

### Sample Transcriptions 
| Dataset | Reference | Prediction |
| --- | --- | --- |
| **Mozilla** | వివిధ సంఘాలు మద్దతు ప్రకటించాయి | వివిధ సంఘాలు మద్దతు ప్రకటించాయి |
| **IndicTTS** | రాజు అలా అనేసరికి సునందుడు చేసేది లేక తలవంచుకొని ఇంటికి వెళ్లిపోయాడు | రాజు అలా అనేసరికి సునందుడు చేసేది లేక తలవంచుకొని ఇంటికి వెళ్లిపోయాడు |
| **OpenSLR** | మధ్యధరా ప్రాంతంచే చుట్టి వున్నది | మధ్యధరా ప్రాంతంచే చుట్టి వున్నది |
