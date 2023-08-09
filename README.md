## 소개
Hugging face에 있는 datasets를 이용해서 한국어 자연어처리에서 사전에 훈련된 모델들에 대한 finetuning은 인터넷상으로는 2021년에 많은 일들이 행해진 것 같다. 그러나, 발행된 한국어 관련 자연어처리 관련 서적들을 보면 Huggingface의 도구들을 쓰는 책으로는 유일하게 이기창의 2021년 이지스 퍼브리싱에서 발행된 *(Do It! Bert와 GPT로 배우는) 자연어 처리: 트랜스포머 핵심 원리와 허깅페이스 패키지 활용법* 이라는 책이 현재(2023.8)로서는 유일하다. 그런데 이책을 보면, ratsnlp라는 패키지를 설치하는 것부터 시작하는데 이 패키지를 폄하할 생각은 없지만, 처음 한국어 처리를 배우고자 하는 사람들에겐 전혀 필요없는 과정이고, 허깅페이스 패키지 활용법이라는 책의 제목과는 상반되는 접근 방법이다. 이책의 단점으로는

- ratsnlp 라는 패키지를 설치하게 되어 있어 활용성이 극히 제한을 받는다.
- datasets를 hugging face에 있는 것을 쓰지 않는다.

이러한 단점으로 인해 한국어 처리에 있어 퇴보를 가져올 수 있기에, 그냥 hugging face에 있는 것만으로 한국어 처리를 하는 작업을 보여주는 것이 필요하기에 이러한 일을 하게 되었다. 이는 이미 많은 다른 이들이 오래전부터 해오던 일이지만 관련 notebook이 올라와 있는 경우도 드물고, 친절한 설명도 없는 것이 단점인데, 여기서는 친절한 설명까지는 부족해도 관련 notebook 파일을 올려놓고자 한다

## Tasks for korean nlp by pipelines
Common NLP tasks

- Token Classification
  - NER (named entity recognition)
    - fine-tuned model: chunwoolee0/klue_ner_roberta_model
    - datasets used: klue-ner
    - pretrained model ckeckpoint: klue/roberta-base
  - Part-of-speech tagging (POS)
- Sequence classification
  - Sentiment Classification
    - fine-tuned model: chunwoolee0/nsmc_roberta_base_model
    - datasets used: nsmc
    - label: ['positive', 'negative']
    - pretrained model ckeckpoint: klue/roberta-base
  - Document Subject Classification
    - fine-tuned model: chunwoolee0/klue_ynat_roberta_base_model
    - datasets used: klue/ynat
    - label: ['IT과학','경제','사회','생활문화','세계',
    '스포츠','정치]
    - pretrained model ckeckpoint: klue/roberta-base
  - Pair Classification
    - fine-tuned model: chunwoolee0/klue_nli_roberta_base_model
    - datasets used: klue/nli
    - sentence1, sentence2
    - label: ['entailment', 'contradiction','neutral]
    - pretrained model ckeckpoint: klue/roberta-base
- Masked Language Modeling
  - pretrained model ckeckpoint: klue/roberta-base
- Summarization
- Translation
- Causal Language Modeling (koGPT-2)
  - Sentence Generation
    - fine-tuned model: chunwoolee0/klue_nli_roberta_base_model
    - datasets used: nsmc
    - pretrained model ckeckpoint: skt/kogpt2-base-v2
- Question Answering


