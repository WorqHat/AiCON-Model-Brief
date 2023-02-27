# AiCON-Model-Brief

## Model details
**Organization developing the model**
[WorqHat (Winlysis Private Limited)](www.worqhat.com)

**Model date**
AiCON was trained between 1st November 2022 and 27th February 2023. However, the dataset that has been used is limited to September of 2022.

**Model version**
This is version 1.0.1 of the model.

**Model type**
AiCON is an Auto-Regressive large language model based on the Transformer neural network architecture that comes in a size of 142 Billion Parameters or 2.81T SentencePiece Tokens.

**Detailed Documentation**
https://sagnikghosh.dev/articles/AiCon-Future-of-AI-Driven-Content-Generation-with-WorqBot/
https://sagnikghosh.dev/articles/future-of-content-generation-with-WorqBot/

**Where to send questions or comments about the model**
Questions and comments about AiCON can be sent via email to [worqbot@worqhat.com](mailto:worqbot@worqhat.com)  or [support@worqhat.com](mailto:support@worqhat.com)

## Factors
**Relevant factors**
One of the most relevant factors for which model performance may vary is which language is used. Although we included 35 languages in majority andseveral other languages in smaller numbers as well in the training data, most of our dataset is made of English text, and we thus expect the model to perform better for English than other languages. Relatedly, it has been shown in previous studies that performance might vary for different dialects, and we expect that it will be the case for our model.

**Evaluation factors**
As our model is trained on data from the Web, we expect that it reflects biases from this source. We thus evaluated on RAI datasets to measure biases exhibited by the model for gender, religion, race, sexual orientation, age, nationality, disability, physical appearance and socio-economic status. We also measure the toxicity of model generations, depending on the toxicity of the context used to prompt the model.

## Metrics
**Model performance measures**
We use the following measure to evaluate the model:
- Accuracy for common sense reasoning, reading comprehension, natural language understanding (MMLU), BIG-bench hard, WinoGender, BLEU Score and CrowS-Pairs,
- Exact match for question answering,

**Approaches to uncertainty and variability**
With the objectives and metrics defined, we describe AiCon’s two-stage training: pre-training and fine-tuning. In the pre-training stage, we first created a dataset of 1.80T words — from public data, conversational snippets from support documents and other public web documents. After tokenizing the dataset into 2.81T SentencePiece tokens, we pre-train the model using GSPMD(General and Scalable Parallelization for ML Computation Graphs) to predict every next token in a sentence, given the previous tokens.

The Fine-Tuning Stage involves training the model to perform a combination of tasks, including generating natural language responses to given prompts and classifying the responses for quality and safety. The goal of the fine-tuning process is to produce a single multi-task model that can both generate appropriate responses and classify them based on their quality and safety. To achieve this, the model is trained on a dialog dataset that consists of back-and-forth exchanges between two authors.

The training process involves two components: the generator and the classifiers. The generator is responsible for predicting the next token in the conversation and generating a response to a given prompt. On the other hand, the classifiers are trained to predict the safety and quality ratings of the response in context, using annotated data.

When the model is used to generate responses, it follows a specific process. Given the multi-turn context of the prompt, the generator generates several candidate responses. The classifiers then predict the safety and quality scores for each candidate response. Responses with low safety scores are immediately filtered out. The remaining candidate responses are re-ranked based on their quality scores, and the highest-ranked response is selected as the final response.

We further improve the quality of the generated responses by filtering the training data used for the generation task with the classifiers. This increases the density of high-quality response candidates and reduces the likelihood of producing low-quality or unsafe responses.

![Classifier Sequential](https://sagnikghosh.dev/static/classifier.jpg)

## Quantitative analysis
Hyperparameters for the model architecture

We present our results on bias in the table below. Note that lower value is better indicating lower bias. 

| No  | Category             | FAIR LLM |
| --- | -------------------- | -------- |
| 1   | Gender               | 63.4     |
| 2   | Religion             | 73       |
| 3   | Race/Color           | 59       |
| 4   | Sexual orientation   | 82       |
| 5   | Age                  | 70.1     |
| 6   | Nationality          | 64.2     |
| 7   | Disability           | 64.7     |
| 8   | Physical appearance  | 77.8     |
| 9   | Socioeconomic status | 73.5     |
|     | AiCON Average        | 77.1     |

*Table 1 - Summary bias of our model output*

## Ethical considerations
**Data**
The data used to train the model is collected from various sources, mostly from the Web. As such, it contains offensive, harmful and biased content. We thus expect the model to exhibit such biases from the training data.

**Human life**
The model is not intended to inform decisions about matters central to human life, and should not be used in such a way.

**Risks and harms**
Risks and harms of large language models include the generation of harmful, offensive or biased content. These models are often prone to generating incorrect information, sometimes referred to as hallucinations. We do not expect our model to be an exception in this regard.

**Use cases**
AiCON is a foundational model, and as such, it should not be used for downstream applications without further investigation and mitigations of risks. These risks and potential fraught use cases include, but are not limited to: generation of misinformation and generation of harmful, biased or offensive content.
