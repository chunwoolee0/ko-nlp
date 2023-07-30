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


