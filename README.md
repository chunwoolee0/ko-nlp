## 소개
Hugging face에 있는 datasets를 이용해서 한국어 자연어처리에서 사전에 훈련된 모델들에 대한 finetuning은 오래 전부터 행해진 것 같다. 그러나, 발행된 한국어 관련 자연어처리 관련 서적들을 보면 Huggingface의 도구들을 쓰는 책으로는 이기창의 2021년 이지스 퍼브리싱에서 발행된 *(Do It! Bert와 GPT로 배우는) 자연어 처리: 트랜스포머 핵심 원리와 허깅페이스 패키지 활용법* 이라는 책이 현재(2023.8)로서는 유일하다. 그런데 이책을 보면, ratsnlp라는 패키지를 설치하는 것부터 시작하는데 이 패키지를 폄하할 생각은 없지만, 처음 한국어 처리를 배우고자 하는 사람들에겐 전혀 필요없는 과정이고, 허깅페이스 패키지 활용법이라는 책의 제목과는 상반되는 접근 방법이다. 이책의 단점으로는

- ratsnlp 라는 패키지를 설치하게 되어 있어 활용성이 극히 제한을 받는다.
- datasets를 hugging face에 있는 것을 쓰지 않는다.

이러한 단점으로 인해 한국어 처리에 있어 퇴보를 가져올 수 있기에, 그냥 hugging face에 있는 것만으로 한국어 처리를 하는 작업을 보여주는 것이 필요하기에 이러한 일을 하게 되었다. 이는 이미 많은 다른 이들이 오래전부터 해오던 일이지만 관련 notebook이 올라와 있는 경우도 드물고, 친절한 설명도 없는 것이 단점인데, 여기서는 친절한 설명까지는 부족해도 관련 notebook 파일을 올려놓고자 한다

## Tasks for korean nlp
Common NLP tasks

- Token Classification
  - NER (named entity recognition)
    문장 내에서 인명(PS), 기관(OG), 장소(LC), 양(QT), 날짜/시간(DT)를 인식해서 꼬리표(named entity recognition)를 달아주는 프로그램이다. 모델 klue/roberta-base를 써서 klue/ner 데이터셋을 가지고 파인튜닝을 한다. klue_ner_roberta_train.ipynb 쥬피터 노트북 참조. 
    - fine-tuned model: chunwoolee0/klue_ner_roberta_model
    - datasets used: klue-ner
    - pretrained model ckeckpoint: klue/roberta-base
  - Part-of-speech tagging (POS)
- Sequence classification
  - Sentiment Classification
    문장을 보고 긍정적인 내용인지, 부정적인 내용인지를 판별하는 프로그램이다. 역시 klue/roberta-base 모델을 써서 nsmc 데이터셋을 가지고 파인튜닝을 한다. doccls_nsmc.ipynb 쥬피터 노트북을 참조바람.
    - fine-tuned model: chunwoolee0/nsmc_roberta_base_model
    - datasets used: nsmc
    - label: ['positive', 'negative']
    - pretrained model ckeckpoint: klue/roberta-base
  - Document Subject Classification
    기사를 보고 IT과학, 경제, 사회, 생활경제, 세계, 스포트, 정치 어떤 분야의 기사인지를 판별하는 프로그램. klue_ynat_train.ipynb를 참조
    - fine-tuned model: chunwoolee0/klue_ynat_roberta_base_model
    - datasets used: klue/ynat
    - label: ['IT과학','경제','사회','생활문화','세계',
    '스포츠','정치]
    - pretrained model ckeckpoint: klue/roberta-base
  - Pair Classification
    전제를 보고 가정이 전제에 따르는지 (entailment), 전제와 모순이 되는지, 관계가 없는지를 판별하는 프로그램. klue_nli_roberta_train.ipynb를 참조
    - fine-tuned model: chunwoolee0/klue_nli_roberta_base_model
    - datasets used: klue/nli
    - sentence1, sentence2
    - label: ['entailment', 'contradiction','neutral]
    - pretrained model ckeckpoint: klue/roberta-base
- Masked Language Modeling
  이 경우는 "대한민국의 대통령은 [MASK] 이다."와 같이 [MASK]를 채우는 문제인데 jklue/bert-base, klue-roberta-base가 이런 목적으로 만들어진 모델이기 때문에 따로 파인튜닝을 하지 않고 이들 모델을 써서 pipeline을 써서 [MASK]를 찾는 일을 수행할 수 있다. 관련된 작업은 ko_nlp_tasks.ipynb 에서 발견할 수 있다. 
  - pretrained model ckeckpoint: klue/roberta-base
- Summarization
  긴 문장이 있어 읽기 힘들 때 이를 간단히 요약하는 일로 ko_nl-_tasks.ipynb 에서 발견할 수 있다. 
- Translation
  영어를 한국어로, 한국어를 영어로 바꾸어주는 프로그램이다. translation_en_kr.ipynb, translation_ko_en.ipynb 참조. 영어를 한국어로 번역하는 pretrained 모델로 Helsinki-NLP/opus-mt-tc-big-en-ko가 작동을 해야 하는데 엉뚱한 결과를 주기 때문에 circulus/kobart-trans-en-ko-v2 를 썼다. 
  - fine-tuned model: chunwoolee0/kd4_opus-mt-ko-en, chunwoolee0/circulus-kobart-en-to-ko
  - datasets used: kde4 en-ko
  - pretrained model ckeckpoint: Helsinki-NLP/opus-mt-ko-en, circulus/kobart-trans-en-ko-v2
- Causal Language Modeling (koGPT-2)
   이런 일을 하기 위해 만들어진 것이 GPT이다. skt/kogpt2-v2를 써서 문장 생성하는 예를 역시 ko_nl-_tasks.ipynb 에서 발견할 수 있다. 
  - Sentence Generation
    - fine-tuned model: chunwoolee0/klue_nli_roberta_base_model
    - datasets used: nsmc
    - pretrained model ckeckpoint: skt/kogpt2-base-v2
- Question Answering
  질문을 하면 주어진 지문(contexts)에서 답을 찾는 프로그램으로 nlp_course_korquad.ipynb를 참조. 데이터 셋이 너무 커서 20000개만 선택. 답은 제대로 찾으나 조퍼리를 못함. 
  - fine-tuned model: chunwoolee0/roberta-keti-air-korquad
  - datasets used: KETI-AIR/korquad v1.0 (v2.0도 있음)
  - pretrained model ckeckpoint: klue/roberta-base


