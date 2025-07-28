For anonymous ARR 2025 July submission.

# Multilingual, Not Multicultural: A Korean Benchmark for the Cultural Empathy Gap

This repository contains the official dataset for **KoED (Korean Empathetic Dialogues)**, a benchmark designed to investigate the gap between multilingual capabilities and multicultural competence in Large Language Models (LLMs).

This work is part of an anonymous submission to ARR 2025 July. The official, non-anonymous repository will be made public upon acceptance.

## 1. Introduction: The Cultural Empathy Gap

While LLMs are increasingly multilingual, it remains unclear if they are truly multicultural. This project challenges the assumption that linguistic fluency equates to cultural understanding. We introduce KoED to provide a controlled environment for empirically measuring what we term the **"cultural empathy gap"**: the systematic performance degradation of LLMs when moving from a familiar (US-centric) cultural context to a novel one (Korean).

KoED is not a direct translation of the English **EmpatheticDialogues (ED)** dataset. Instead, it is a meticulous **cultural reconstruction**, designed to test for genuine cultural reasoning beyond surface-level language processing.

## 2. Dataset Description

KoED provides a parallel corpus for cross-cultural evaluation. Each entry includes a situation, a culturally reconstructed Korean dialogue, its English counterpart, and multi-label emotion annotations.

### Key Features

-   **Cultural Reconstruction**: Dialogues are not just translated but adapted to reflect authentic Korean social norms, interactional styles, and cultural scripts.
-   **Emotional Granularity**: A multi-label annotation scheme captures the complex, mixed feelings of real-world conversations, resulting in 555 unique emotion combinations.
-   **Parallel Structure**: The direct parallel to the ED dataset allows for controlled experiments that isolate the impact of cultural context.
-   **Culture-Specific Concepts**: Includes handcrafted dialogues for key cultural concepts like ‘jeong’ (정; 情) and ‘han’ (한; 恨) that lack direct English equivalents.

### Data Format

Each entry consists of a conversation ID, situation, emotion labels, and the dialogue itself.

```json
{
  "conv_id": "hit:46_conv:92",
  "ko_situation": "오늘 내 생일이야. 누가 축하 메시지 보낼 지, 무슨 선물을 받을 지 기대돼.",
  "situation": "Today is my birthday. I can't wait to see who calls me. Or my gifts.",
  "emotion": [
    "excited",
    "anticipating"
  ],
  "dialogue": [
    {
      "utter_idx": 1,
      "ko_utter": "오늘 내 생일이야! 서른넷 됐어!",
      "utter": "Today is my birthday! I am 34!",
      "user_id": 27.0
    },
    {
      "utter_idx": 4,
      "ko_utter": "아, 그렇구나. 생일을 2번 즐길 수 있네! 그럼 지금 카톡 알림음 들릴 때마다 설레겠다.ㅎㅎ 그나저나 아침에 미역국은 먹었어?",
      "utter": "I hope you get lots and lots! ",
      "user_id": 11.0
    }
  ]
}
'''

### Dataset Statistics

| Statistic                   | Value |
| --------------------------- | ----- |
| Total Dialogues             | 1,360 |
| Emotion Categories          | 34    |
| Dialogues per Category      | 40    |
| Unique Emotion Combinations | 555   |

## 3. Dataset Construction Pipeline

Our construction process was designed for maximum methodological rigor, inspired by the cultural adaptation paradigm from KoBBQ (Jin et al., 2024).

1.  **Initial Translation**: The ED dataset was first translated using GPT-4o.
2.  **Cultural Categorization**: Two expert annotators (the first authors of the paper) categorized each dialogue as:
    -   `SIMPLY-TRANSFERRED`: Culturally neutral and directly transferable.
    -   `CONTEXT-MODIFIED`: Requiring adaptation of the context, situation, or social norms.
    -   `SAMPLE-REMOVED`: Deeply rooted in US-specific culture with no Korean equivalent.
3.  **Reconstruction & Annotation**: A rigorous, three-stage process was performed by the authors for all included dialogues:
    -   **Stage 1 (Independent Work)**: Each author independently reconstructed half of the dialogues and simultaneously performed multi-label emotion annotation.
    -   **Stage 2 (Cross-Check)**: The authors cross-validated each other's reconstructions and annotations.
    -   **Stage 3 (Joint Review)**: Disagreements were resolved in a joint session to reach a final consensus.
4.  **Handcrafting**: 80 new dialogues for 'jeong' and 'han' were handcrafted to serve as unambiguous, single-label test cases for culture-specific concepts.

## 4. How to Use this Benchmark

KoED is designed as a benchmark **solely for evaluation**, not for model training. It encourages a standardized, zero-shot evaluation setting.

-   **Probing the Cultural Empathy Gap**: Compare a model's performance on the original ED dataset vs. the KoED dataset.
-   **Evaluating Data Provenance Effect**: Compare the performance of Western-centric models (e.g., Llama) vs. Korean-specialized models (e.g., EXAONE).
-   **Testing Cultural Knowledge**: Evaluate a model's ability to recognize and respond to culturally-specific concepts like 'jeong' and 'han'.

## 5. Evaluation Framework

We propose a holistic evaluation framework with five key metrics. The full rubrics are provided in the paper's appendix.

-   **Explorations (EX)**: How deeply the model explores the user's situation and emotions.
-   **Interpretations (IP)**: How accurately the model understands and interprets the user's emotions.
-   **Emotional Reactions (ER)**: How appropriate the model's emotional reaction is.
-   **Evoked Emotion Alignment (EEA)**: How similar the model's response is to a typical human response.
-   **Cultural Appropriateness (CA)**: (Our primary metric) How well the model reflects the target culture's norms and linguistic precision.

## 6. License

**IMPORTANT:** The KoED dataset is a derivative work of the EmpatheticDialogues (ED) dataset. As such, it inherits its license. KoED is provided under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) license**.

-   You are free to share and adapt the material for **non-commercial** purposes.
-   You must give appropriate credit (e.g., cite our paper).

Please refer to the full CC BY-NC 4.0 license for details.

## 7. Citation

If you use KoED in your research, please cite our paper (details to be added upon acceptance).
