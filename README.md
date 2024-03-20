# On the Dangers of Stochastic Parrots: Can Language Models Be Too Big? 🦜

> Authors: Emily M. Bender, Timnit Gebru, Angelina McMillan-Major, Shmargaret Shmitchell

> Published: March 1st, 2021



## Introduction

In recent years, the field of Natural Language Processing (NLP) has witnessed a significant shift towards the development of increasingly larger language models (LMs), with BERT, GPT-2/3, and others pushing the boundaries of what's possible in understanding and generating human language. The paper "On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?" by Emily M. Bender, Timnit Gebru, Angelina McMillan-Major, and Shmargaret Shmitchell critically examines this trend, posing the essential question: **How big is too big?**

This work delves into the potential risks associated with the deployment of massive LMs, such as environmental and financial costs, biases encoded in training data, and the consequent societal impacts. By highlighting these concerns, the paper suggests researchers and developers to weigh the trade-offs between model size and utility and to explore more sustainable and ethical approaches in advancing language technology.

## Background

**1. Transition from N-gram to Neural Models:**

![image](https://github.com/jinoh0731/Can-Language-Models-Be-Too-Big-/assets/111295393/d3584807-8639-4a23-8695-db4f6da2d71b)


Early LMs relied on n-gram models that required substantial data but had limitations in capturing longer dependencies. The paper notes the progression to neural models, which provided a foundational shift in handling language processing tasks, notably through pretrained word embeddings and LSTM models that significantly reduced the need for labeled data in supervised tasks.

**2. Advent of Transformer Models:**

The paper points to a significant leap with the development of Transformer models, which benefited from larger architectures and vast amounts of training data, marking a departure from earlier models by continuously improving performance on a range of NLP tasks. This era witnessed the introduction of models such as BERT, GPT-3, and others, which are characterized by their unprecedented scale in terms of parameters and the datasets they are trained on.

**3. Trend Towards Larger Models:**

An observed trend is the race towards creating **ever larger models**, evidenced by a table listing various models along with their sizes and the datasets used for training. This trend is underscored by the collection of massive text corpora from the web and the performance gains associated with increasing model and data size.

![Screenshot 2024-03-17 at 9 44 09 PM](https://github.com/jinoh0731/Can-Language-Models-Be-Too-Big-/assets/111295393/3a9d2668-7d62-4806-ba82-c998995d562a)



## Environmental and Financial Cost

### Environmental Cost

![image](https://github.com/jinoh0731/Can-Language-Models-Be-Too-Big-/assets/111295393/86fc83a4-82b4-4686-b1d0-a97bb658f3d5)

 Training state-of-the-art language models (LMs) has significant environmental costs, particularly in terms of carbon emissions. The energy required for training these models, especially those with large amounts of data and parameters, is substantial. 
 > Training a single BERT based model (without hyperparameter tuning) on GPU can result in carbon emissions equivalent to a trans-American flight.

This is because the compute resources typically used in the cloud are not primarily sourced from renewable energy, and even when they are, renewable energy sources can still be costly to the environment. Financially, the costs erect barriers to entry, limiting who can contribute to the research area and potentially creating a divide between those with resources and those without. As a consequence, the negative effects of climate change disproportionately impact the world's most marginalized communities, who are least likely to benefit from the technology.

<details>
  <summary><b>Question 1: Which factor from the large language model could lead to environmental cost?</b></summary>
  <br> 

  - **Complex Computation Across Millions and Billions of Parameters:** This requires substantial computational power over extended periods, often days or weeks, depending on the size of the model and the dataset.
  - **Data Center Energy Use:** The computational resources needed to train these models are typically housed in data centers, which consume large amounts of electricity to power the servers and the necessary cooling systems to keep the equipment at optimal temperatures. While some of this energy might come from renewable sources, a significant portion still comes from fossil fuels, directly contributing to CO2 emissions.
  - **Repeated Training Cycles:** Training a large model isn't a one-time process. It often requires multiple iterations to fine-tune the parameters and validate the model's performance. Each training cycle consumes more energy, adding to the overall carbon footprint.
  - **Infrastructure and Network Traffic:** Beyond the direct computational requirements, supporting infrastructure, including network data transfers to and from cloud services (where much of this training occurs), adds to the total energy consumption.
 
</details>

### Financial Cost

![image](https://github.com/jinoh0731/Can-Language-Models-Be-Too-Big-/assets/111295393/f0c23534-bde1-4980-8b8f-fff0434c80d0)

- **Infrastructure Cost**: Necessitates investment in powerful computing infrastructure, including high-performance GPUs or TPUs, which are expensive to purchase and maintain.

- **Financial Barriers**: The cost associated with the compute necessary for creating large LMs creates barriers to entry, centralizing power among those with access to significant resources.

- **Inequity and Accessibility**: The benefits of LMs often do not reach marginalized communities, yet these communities may disproportionately bear the environmental impacts.
 
- **Continual Model Training and Updating**: To maintain the relevance and performance of LMs, continuous training and updating are necessary, especially as language and societal norms evolve. This ongoing process demands sustained financial investment in computational resources and energy consumption.

To address these concerns, researchers recommend:

- Prioritizing energy-efficient architectures.
- Reporting training times and sensitivity to hyperparameters for reproducibility and fairness.
- Supporting initiatives for computationally efficient algorithms.
- Advocating for government investment to democratize access to compute resources.


## Large Data != Unbiased Data

### Size Doesn't Guarantee Diversity

The authors discuss how the internet's vastness and the diversity of its content might suggest that large datasets would be representative of varied perspectives. However, they point out that several factors, such as internet access disparities and selective data scraping methodologies, result in datasets that primarily reflect dominant viewpoints. This overrepresentation of hegemonic perspectives leads to models that further amplify existing biases.

**Inclusion and Multilinguality Concerns:**

Despite advancements, the paper raises concerns about the inclusivity of these models, noting that the majority of the world's languages are underrepresented in technological advancements, and models like mBERT and GPT-3, despite their multilingual data, do not sufficiently address the language support gap.

**Example 1: mBERT (Multilingual BERT):**
> 
> While mBERT is trained on Wikipedia text from 104 languages, the quality of the model’s performance is not uniform across all these languages. It tends to perform well on languages that have a large presence in the training data (like English, Chinese, or Spanish), but much worse on low-resource languages that have less representation in the dataset. This is due to a phenomenon known as the "Matthew effect" in machine learning, where "rich get richer," meaning that languages with more data available benefit more from the training process.
> 
> [Code Demo](https://github.com/jinoh0731/Can-Language-Models-Be-Too-Big-/blob/main/paper_code_demo.ipynb)

#### mBERT

- Number of Parameters: 178 Million
- Number of Layers 12 transformer layers
- Model Type: Transformer-based model, specifically utilizing the BERT (Bidirectional Encoder Representations from Transformers) architecture adapted for multiple languages.
- Hidden Size: 768 units in the hidden layers
- Self-Attention Heads: 12 attention heads in each transformation block


**Example 2: GPT-3:**
> 
>  Even though 7% of GPT-3's training data includes non-English texts, this does not guarantee equitable performance across languages. The model’s capabilities in generating and understanding text can still be disproportionately better in English due to the vast majority of its training data being English. Additionally, the nuances, idiomatic expressions, and cultural contexts of other languages may not be well captured, leading to outputs that are less accurate or appropriate when the model is used for languages other than English.

#### GPT-3

- Number of Parameters: 175 billion parameters.
- Number of Layers: GPT-3 consists of 96 transformer layers.
- Model Type: Transformer-based model, specifically utilizing a decoder-only architecture from the Generative Pre-trained Transformer series, optimized for autoregressive language generation.
- Hidden Size: 12,288 units in the hidden layers.
- Self-Attention Heads: 96 attention heads in each transformer block.

### Static Data/Changing Social Views

Static training datasets cannot capture the dynamic nature of social views and language use. The authors highlight the risk of "value-lock," where models trained on outdated data may not reflect current social norms or understandings, potentially causing harm by perpetuating outdated stereotypes or misrepresenting social movements.

### Encoding Bias

Large, uncurated datasets inherently encode biases, including stereotypes and derogatory associations, which are then learned by LMs. These biases can manifest in subtle ways, such as through language that reinforces stereotypes or through the omission of perspectives from marginalized groups. The risks of harm are significant, as these biases can lead to the further marginalization of already vulnerable populations.

> Example 3: **GPT-2 Gender Bisas:**
>
> GPT-2's training data is sourced by scraping outbound links from Reddit, and Pew Internet Research's 2016 survey reveals 67% of Reddit users in the United States are men, and 64% between ages 18 and 29. Furthermore, Gehman et al. show that GPT-2's training data also finds 272,000 documents from unreliable news sites and 63,000 frim banned subreddits.
>
> [Code Demo](https://github.com/jinoh0731/Can-Language-Models-Be-Too-Big-/blob/main/paper_code_demo.ipynb)

#### GPT-2

- Number of Parameters: 1.5 Billion
- Number of Layers: 48 transformer layers
- Model Type: Transformer-based model, specifically utilizing a decoder-only architecture from the Generative Pre-trained Transformer series, optimized for autoregressive text generation.
- Hidden Size: 1600 units in the hidden layers
- Self Attention Head: 25 heads in each transformer block

  
### Curation Documentation & Accountability

Investing resources into the careful curation and documentation of training datasets is important. The paper advocates for a move away from simply amassing large quantities of data towards a more thoughtful process of dataset creation. This includes documenting the data collection process, the motivations behind it, and the potential biases within the data. Such practices are essential for creating more equitable and less harmful language technologies.

## Understanding the Risks: The "Stochastic Parrots" Dilemma 🦜

Despite their sophistication, large LMs do not understand the text they generate. Like parrots, they mimic human language based on patterns seen during their training, without grasping the meaning behind the words.
Therefore, the text produced by LMs can be convincingly human-like, leading people to overestimate the models' understanding. This poses a risk of misinterpretation, where the output is taken as thoughtful or meaningful communication when it is not. As discussed above, training data for LMs often reflect the biases present in society. These models, therefore, risk perpetuating and even amplifying these biases, contributing to a cycle of reinforcement that can deepen societal divides. Given their ability to generate plausible text, LMs could be exploited by individuals with harmful intentions, such as spreading misinformation or creating divisive content on a large scale. Also, LMs trained on vast datasets can inadvertently memorize and reproduce sensitive personal information, posing a risk to individual privacy. Lastly, when used for language translation, LMs might produce fluent but inaccurate translations. The seeming coherence of these translations can mislead users into trusting incorrect or misleading information.

## Path Forward

### Ethical Consideration and Planning: 

Encourages the incorporation of ethical considerations in the early stages of model development to anticipate and mitigate potential harms.

### Prioritizing Energy Efficiency: 

Urges the development of models that are not only powerful but also energy-efficient to reduce environmental impact.

### Focusing on Data Quality Over Quantity: 

Highlights the importance of carefully curated and documented datasets rather than simply amassing large quantities of data, to improve model quality and fairness.

### Engaging with Stakeholders: 

Recommends involving diverse stakeholders, including those from marginalized communities, in the development process to ensure technology benefits are more evenly distributed.

### Exploring Alternative Models: 

Suggests investigating models and methods that achieve high performance without the need for excessive computational resources or data, fostering innovation and inclusivity.

### Acknowledging the Risks: 

Reiterates the potential harms associated with large LMs, including the perpetuation of biases, privacy concerns, and the risk of misuse.

### Calling for Responsible Research: 

Emphasizes the need for the research community to prioritize ethical considerations, engage with a broader range of stakeholders, and explore more sustainable and inclusive approaches to language technology development.

### Looking Towards a Balanced Future: 

Encourages a balanced approach that considers the trade-offs between technological advancements and their impacts, aiming for progress that benefits society as a whole.

# Critical Analysis

- **Deep Exploration of Bias Perpetuation:** While the paper discusses biases encoded in large datasets, it could explore more deeply how these biases are perpetuated and the long-term societal impacts. For example, authors could examine case studies where biases in training data have led to real-world discriminatory outcomes, such as in automated hiring tools or predictive policing software. This would help underline the tangible societal impacts of these biases.

- **Providing Clear Guideline**: Although various potential harms are identified, further development could involve a more nuanced discussion on how these harms can be systematically identified, prevented, or mitigated in the design and deployment of LMs by providing the outline of specific design principles for ethical AI, such as transparency, accountability, and fairness. For example, introduce guidelines for transparency in AI systems that require models to provide explanations for their outputs, making it easier to identify and correct biases. Recommend establishing oversight bodies with the authority to review and regulate NLP applications, particularly those used in sensitive areas like healthcare, law enforcement, and employment.

- **Large Language Model's Capability**: Because the paper focuses on large language model's downside, it may not fully highlight the transformative capabilities these models bring to the field of natural language processing (NLP) and various applications. Large LMs like GPT-3, GPT-4 and other, have achieved outstanding performance on a broad spectrum of NLP tasks, and introduced groundbreaking advancements such as few-shot learning, demonstrating a deep understanding of language patterns. Furthermore, they've enabled innovative applications across different domains, from enhancing conversational AI to accelerating scientific discovery, and democratized AI development by providing access to cutting-edge technology. Balancing the recognition of these significant achievements with the critical evaluation of associated risks is essential for guiding the future of AI towards sustainable, equitable, and responsible development.

- **Consideration of Cost-Efficiency:** While discussing the drawbacks of large language models (LMs), it's important to acknowledge that their usage can sometimes result in cost-efficient solutions for certain tasks. For instance, in multilingual applications, utilizing a model like mBERT can significantly reduce costs compared to deploying separate language-specific models like BERT-base for each language. This cost-effectiveness stems from mBERT's ability to leverage shared parameters across languages, reducing the need for additional training sessions and infrastructure. Therefore, in scenarios where cost is a critical factor, opting for a large LM with multilingual capabilities can offer an economically advantageous solution without compromising performance.

> Multilingual BERT (mBERT) is a groundbreaking extension of the original BERT model, pre-trained on a large corpus comprising text from 104 different languages. This model maintains the powerful architecture of BERT while expanding its applicability to a wide range of languages without the need for language-specific model training. mBERT is designed to understand and generate text across languages, making it an invaluable asset for global NLP applications. By leveraging the same transformer architecture as BERT but with training data from multiple languages, mBERT efficiently processes and understands text in languages for which large datasets might not exist, facilitating more inclusive and diverse NLP solutions. This makes mBERT exceptionally versatile and crucial for tasks like machine translation, cross-lingual classification, and multilingual question answering.

#### mBERT VS BERT

  | Feature               | mBERT                           | BERT-base                         |
|-----------------------|---------------------------------|-----------------------------------|
| Number of Parameters  | 178 Million                     | 110 Million                       |
| Number of Layers      | 12 transformer layers           | 12 transformer layers             |
| Model Type            | Transformer-based model, specifically utilizing the BERT architecture adapted for multiple languages. | Transformer-based model, utilizing a bidirectional encoder architecture. |
| Hidden Size           | 768 units in the hidden layers  | 768 units in the hidden layers    |
| Self-Attention Heads  | 12 attention heads in each transformation block | 12 attention heads in each transformation block |
| Training Data Scope           | Multilingual (104 languages)                                          | Monolingual (typically English)                        |


<details>
  <summary><b>
Question 2: If you want to do translation task using mBERT or BERT, just by looking at above table, which model would cost less?
   
**HINT** : We are trying to do the multi-lingual task !
  
  </b></summary>
  <br> 

mBERT would cost less for translation tasks due to its multilingual training scope and shared parameters across languages. Utilizing mBERT enables efficient use of computational resources. Additionally, mBERT's deployment efficiency is higher as a single model serves multiple languages, reducing the need for separate models, thereby decreasing overall costs in multilingual applications. Overall, mBERT offers cost savings in training and deployment for translation tasks compared to BERT-base, which is primarily trained for monolingual tasks.


| Feature               | mBERT                           | BERT-base                         |
|-----------------------|---------------------------------|-----------------------------------|
| Number of Parameters  | 178 Million                     | 110 Million                       |
| Number of Layers      | 12 transformer layers           | 12 transformer layers             |
| Model Type            | Transformer-based model, specifically utilizing the BERT architecture adapted for multiple languages. | Transformer-based model, utilizing a bidirectional encoder architecture. |
| Hidden Size           | 768 units in the hidden layers  | 768 units in the hidden layers    |
| Self-Attention Heads  | 12 attention heads in each transformation block | 12 attention heads in each transformation block |
| Training Data Scope           | Multilingual (104 languages)                                          | Monolingual (typically English)                        |
| Training Resource Efficiency  | Higher, due to shared parameters across languages | Lower, as it is trained specifically for one language and requires separate models for each language for multilingual support. |
| Deployment Efficiency | Higher, a single model serves multiple languages, reducing the need for multiple models in multilingual applications. | Lower, requires separate models for each language, increasing resource use in multilingual settings. |
| Potential for Reducing Redundancy | High, leverages linguistic similarities across languages, potentially making training more efficient. | N/A, as it focuses on a single language, missing out on cross-lingual efficiencies. |
| Eco-friendliness in Application | Potentially higher, as deploying one model for many languages can save on computational resources in serving global users. | Potentially lower for global applications, as it would require deploying multiple language-specific models. |
| Transfer Learning Efficiency | High, as it can be fine-tuned for specific languages or tasks with minimal additional training. | Moderate, fine-tuning is also possible but within the scope of its trained language. |
| Training Costs for Multi-language | Low, leveraging a single model across multiple languages, reducing the need for separate training sessions and infrastructure| High, deploying separate BERT models for each language in a multilingual setting would cumulatively increase costs. |

 
</details>






#### Psudocode for mBERT

```
Algorithm: mBERT Fine-Tuning for Multilingual Task Learning

/* Fine-tuning a pre-trained multilingual BERT (mBERT) model for a specific NLP task across multiple languages */

Input:
  - Tasks, a set of NLP tasks (e.g., text classification, named entity recognition)
  - D_L, a distribution over languages
  - D_T, a distribution over task-specific training data for each language in D_L
  - k, the number of examples per task per language for fine-tuning
  - LossFunction, the task-specific loss function (e.g., cross-entropy for classification)

Hyperparameters:
  - η, learning rate
  - batch_size, number of examples per training batch
  - total_steps, total number of training iterations

Parameters:
  - θ_pre, pre-trained mBERT model parameters
  - θ_task, task-specific model parameters to be learned

Output:
  - θ*, optimized task-specific model parameters after fine-tuning

Procedure:
1: Initialize task-specific parameters θ_task randomly
2: θ ← θ_pre ∪ θ_task  // Combine pre-trained mBERT parameters with task-specific parameters
3: for step in 1 to total_steps do
4:     Initialize batch_loss to 0
5:     for batch_index in 1 to batch_size do
6:         L ← sample language from D_L
7:         T ← sample task from Tasks
8:         X, Y ← sample k examples and their labels from D_T for task T and language L
9:         y_hat ← mBERT(X, θ)  // mBERT's prediction for the input X
10:        loss ← LossFunction(y_hat, Y)
11:        batch_loss ← batch_loss + loss
12:    end for
13:    average_loss ← batch_loss / batch_size
14:    θ_task ← θ_task - η * gradient(average_loss with respect to θ_task)  // Update only the task-specific parameters
15: end for
16: return θ* ← θ_pre ∪ θ_task  // Return the fine-tuned model parameters

/* End Algorithm */
```

# Additional Resource

Samuel Gehman, Suchin Gururangan, Maarten Sap, Yejin Choi, and Noah A. Smith. 2020. RealToxicityPrompts: Evaluating Neural Toxic Degeneration in Language Models. In Findings of the Association for Computational Linguistics: EMNLP 2020. Association for Computational Linguistics, Online, 3356–3369. https://doi.org/10.18653/v1/2020.findings-emnlp.301

Ronan Le Bras, Swabha Swayamdipta, Chandra Bhagavatula, Rowan Zellers, Matthew E Peters, Ashish Sabharwal, and Yejin Choi. 2020. Adversarial Filters of Dataset Biases. In Proceedings of the 37th International Conference on Machine Learning.

Emma Strubell, Ananya Ganesh, and Andrew McCallum. 2019. Energy and Policy Considerations for Deep Learning in NLP. In Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics. 3645–3650.

Anna Rogers, Olga Kovaleva, and Anna Rumshisky. 2020. A Primer in BERTology: What We Know About How BERT Works. Transactions of the Association for Computational Linguistics, Vol. 8, 842–866.

"The #BenderRule: On Naming the Languages We Study and Why It Matters" by Emily Bender for Gradient Pub https://thegradient.pub/the-benderrule-on-naming-the-languages-we-study-and-why-it-matters/

"Tackling AI’s Climate Change Problem" by Niklas Sundberg on MIT Sloan Management Review https://sloanreview.mit.edu/article/tackling-ais-climate-change-problem/

# Citation
https://turhancankargin.com/2023/04/04/the-rise-of-large-language-models-and-ai-investment/

Bender, E. M., Gebru, T., McMillan-Major, A., & Shmitchell, S. (2021). On the Dangers of Stochastic Parrots: Can Language Models Be Too Big? Proceedings of the 2021 ACM Conference on Fairness, Accountability, and Transparency (FAccT '21), 610–623. https://doi.org/10.1145/3442188.3445922
