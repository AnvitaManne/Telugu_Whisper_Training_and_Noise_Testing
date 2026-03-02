# Telugu Whisper Training and Noise Testing

This repository includes the fine-tuning of OpenAI’s **Whisper-Small** model for Telugu Automatic Speech Recognition (ASR), followed by a structured evaluation on a large corpus of noise-augmented speech. Training and experimentation were conducted using NVIDIA A40 GPUs on RunPod. 

---

## Hardware and Environment

* **Platform:** RunPod
* **GPU:** NVIDIA A40 (48 GB VRAM)
* **Runtime:** CUDA-enabled Linux environment
* **Framework:** PyTorch + Hugging Face Transformers
* **Precision:** FP16 Mixed Precision Training
All required dependencies are listed in `requirements.txt`.

---

## Model Fine-Tuning

The base model (`openai/whisper-small`) was fine-tuned to optimize transcription accuracy for Telugu speech.

### Training Configuration

* **Optimizer:** RMSProp
* **Learning Rate:** 1e-5
* **Batch Size:** 16
* **Epochs:** 20
* **Evaluation Metrics:** WER, CER

---

## Evaluation against Noise

To test real-world robustness, the model was benchmarked against the Telugu-Noisy-Data corpus, which consists of speech from Mozilla Common Voice, IndicTTS, and OpenSLR augmented with ESC-50 environmental noise (rain, wind, urban sounds).

### Results 

| Metric                    | Result     |
| ------------------------- | ---------- |
| **Total Files Processed** | 7,368      |
| **Global Corpus WER**     | **13.97%** |
| **Global Corpus CER**     | **3.54%**  |

### Sample Transcriptions

| Dataset      | Reference                                                            | Prediction                                                           |
| ------------ | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Mozilla**  | వివిధ సంఘాలు మద్దతు ప్రకటించాయి                                      | వివిధ సంఘాలు మద్దతు ప్రకటించాయి                                      |
| **IndicTTS** | రాజు అలా అనేసరికి సునందుడు చేసేది లేక తలవంచుకొని ఇంటికి వెళ్లిపోయాడు | రాజు అలా అనేసరికి సునందుడు చేసేది లేక తలవంచుకొని ఇంటికి వెళ్లిపోయాడు |
| **OpenSLR**  | మధ్యధరా ప్రాంతంచే చుట్టి వున్నది                                     | మధ్యధరా ప్రాంతంచే చుట్టి వున్నది                                     |

---
