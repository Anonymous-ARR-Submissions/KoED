# KoED
For anonymous ARR 2025 july submission.

# KoED: Korean Benchmark for Culturally Aligned Empathetic Dialogue

## Introduction

KoED (Korean Benchmark for Culturally Aligned Empathetic Dialogue) is a benchmark dataset constructed by Anonymous NLP Lab, designed to evaluate the ability of Large Language Models (LLMs) to generate empathetic dialogues within Korean cultural contexts. Empathy is essential for AI to integrate naturally into human interactions, and KoED overcomes the limitations of existing English-centric datasets (e.g., EmpatheticDialogues) by providing dialogues that reflect Korean culture and emotional expressions.

Official repository: \[Anonymous Repository\] (To be uploaded upon review completion.)

## Dataset Description

KoED includes Korean dialogues tailored to Korean cultural contexts along with English translations, providing emotion labels and dialogue turns that capture unique Korean sentiments and situations.

### Dataset Features

- **Cultural Context**: Reflects Korean local concepts and social values
- **Emotion Labels**: Supports multi-labeling for complex emotional expressions
- **Parallel Structure**: Provides Korean-English dialogue pairs

### Data Format

Each entry consists of a conversation ID, situation description, emotion labels, and dialogue turns. Below is an example:

```json
{
  "conv_id": "hit:24_conv:49",
  "ko_situation": "어렸을 때 놀이공원에 간다는 소식을 들었을 때.",
  "situation": "When I was little and I found out that we were going to the amusement park.",
  "emotion": [
    "excited",
    "nostalgic"
  ],
  "dialogue": [
    {
      "utter_idx": 1,
      "ko_utter": "야, 너도 어렸을 때 부모님이 놀이공원 간다고 하면 엄청 신났었지 않아?",
      "utter": "Hey, didn't you get super excited too when your parents said we're going to the amusement park as a kid?",
      "user_id": 34.0
    },
    {
      "utter_idx": 2,
      "ko_utter": "헐, 맞아! 나 그때 진짜 잠도 못 자고 기다렸던 거 같아. 너는 어디 갔었어?",
      "utter": "OMG, yes! I couldn't even sleep because I was so excited. Where did you go?",
      "user_id": 33.0
    },
    {
      "utter_idx": 3,
      "ko_utter": "나 롯데월드랑 에버랜드 번갈아 가곤 했어. 지금 생각해보면 진짜 좋은 추억이더라. 회전목마 타고, 츄러스도 먹고...",
      "utter": "I used to alternate between Lotte World and Everland. Looking back, those are really fond memories—riding the carousel, eating churros...",
      "user_id": 34.0
    },
    {
      "utter_idx": 4,
      "ko_utter": "진짜 소중한 추억이네. 나도 부모님이랑 놀이공원 간 거 생각하면 괜히 뭉클해.",
      "utter": "Those are really precious memories. Thinking about going to the amusement park with my parents makes me feel emotional too.",
      "user_id": 33.0
    }
  ]
}
```

### Dataset Statistics

- **Emotion Categories**: 34 emotion categories (32 from EmpatheticDialogues plus uniquely Korean emotions "정(情)" and "한(恨)")
- **Dialogue Samples**: 1,360 high-quality dialogue samples (40 samples per emotion category)
- **Average Utterances**: 5.75 utterances per dialogue

## Dataset Construction

KoED was constructed through the following process:

- **Initial Translation**: GPT-4o was used for initial translation of the original English dialogues from EmpatheticDialogues.
- **Cultural Adaptation**: The authors refined translations to ensure Korean cultural context using three methodologies, inspired by the approach proposed in KoBBQ: Korean Bias Benchmark for Question Answering (Jin et al., 2024):
  - 'Simply-Transferred'
  - 'Sample-Removed'
  - 'Context-Modified' (a new methodology replacing 'Target-Modified')
- **Quality Verification**: Multiple validation stages to ensure naturalness and cultural appropriateness.
- **Additional Labeling**: Multi-label approach to capture complex emotional states.

## Usage

KoED can be utilized for the following purposes:

- **Evaluating Cultural Understanding**: Measuring multilingual LLMs' understanding of Korean culture.
- **Emotion Recognition**: Predicting various emotions in dialogues, including uniquely Korean emotions.

## Evaluation Rubrics

Our rubrics for model evaluation:

- **Explorations (EX)**: How deeply the model explores the conversation partner's situation and emotions.
- **Interpretations (IP)**: How accurately the model understands and interprets the partner's emotions and situation.
- **Emotional Reactions (ER)**: How appropriate the model's emotional reaction is to the situation.
- **Evoked Emotion Alignment (EEA)**: How similar the model's emotional response is to typical human responses.
- **Cultural Appropriateness (CA)**: How well the model reflects Korean/English cultural contexts, customs, and social norms.

## Installation and Access

For inquiries, please contact the anonymous submission contact provided in the ARR submission portal.

## Contributors

Authors (Anonymous Institution)

## License

KoED is provided under the CC-BY-SA (Creative Commons Attribution-ShareAlike) license:

- **Attribution**: Proper attribution required (e.g., "KoED by Anonymous NLP Lab")
- **ShareAlike**: Modifications and distributions must be under the same license
- **Ownership**: All rights are held by the Anonymous NLP Lab

For more details, refer to the CC-BY-SA license.
