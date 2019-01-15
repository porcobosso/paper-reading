# reading《Universal Language Model Fine-tuning for Text Classification》

## Contributions 

- model：achieve CV-like transfer learning
- skill：`discriminative fine-tuning` `slanted triangular learning rates` `gradual unfreezing` 
- performance： 6 text-classification task，18%-24% error reduction
- sample-efficient,  ablation analysis ??
- pretrained model, code available

## Related work

### transfer learning in CV

fine-tune first layer of general model  ==>  fine-tune several of the last layers

### hyper columns ??

recently go beyond transferring word embedding

embedding as feature

in CV , hyper columns  ==> end-to-end fine-tune

### multi-task learning 

trained from scratch 

### fine-tuning

 success in similar task, failed in unrelated ones

## Universal Language Model Fine-tuning 

- transfer learning for NLP

  for source task, target task, improve performance  target task

- language modeling in NLP   =  ImageNet in CV

  captures: `long-term dependencies ` `hierarchical relations` `sentiment `

- universal means

  - work across task
  - single architecture and training
    process 
  - no custom feature engineering or preprocessing needed
  - no additional in-domain documents or labels  required

- steps

  - a) General-domain LM pretraining 
  - b) target task LM fine-tuning 
  - c) target task classifier fine-tuning

### General-domain LM pretraining

trained on Wikitext-103 

### target task LM fine-tuning 

#### Discriminative fine-tuning 

`idea`    different layer different info  ==> different extents fine-tune  ==> different  learning rate for each layers

`method`   
$$
\theta^l_t = \theta^l_{t-1} - \eta^l\triangledown_{\theta^l} J(\theta)
$$

$$
\eta^{l-1} = \eta^l/2.6
$$

