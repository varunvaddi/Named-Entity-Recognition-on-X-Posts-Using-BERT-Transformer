# Named-Entity-Recognition-on-X-Posts-Using-BERT-Transformer
### **Named Entity Recognition (NER) on X Posts Using BERT Transformer**

**Project Overview:**
This project involved applying Named Entity Recognition (NER) on a dataset of 11,090 manually tagged tweets, utilizing a BERT-based transformer model to identify and classify various types of entities in social media posts (specifically from X, formerly known as Twitter). The primary goal was to extract meaningful entities such as names, locations, dates, organizations, and monetary values, which can provide valuable insights for various applications like social media analysis, sentiment analysis, and information extraction.

### **Data and Entity Types:**
The dataset comprised 11,090 tweets that were manually annotated with 7 distinct entity types:

1. **NORP (Nationalities, Religious and Political Groups)** – Identifies mentions of nationalities, religious groups, and political entities. For example, "American," "Muslim," "Republican."
2. **PERSON** – Identifies individual or group names, including both public figures and anonymous individuals. For example, "Elon Musk," "the president."
3. **LOC (Location)** – Refers to physical locations such as countries, cities, landmarks, or regions. For example, "Paris," "Mount Everest."
4. **GPE (Geopolitical Entity)** – Represents political entities such as countries, cities, or regions with political boundaries. For example, "United States," "London."
5. **DATE** – Identifies dates, including specific days, months, years, or time-related terms. For example, "January 1st," "2025."
6. **MONEY** – Represents monetary amounts, including currency symbols and numeric values. For example, "$50," "€1000."
7. **ORG (Organization)** – Recognizes named organizations, such as companies, institutions, and governmental organizations. For example, "NASA," "Apple."

The entities mentioned above are vital for understanding the content of the tweets, allowing for deeper insights into public opinion, trends, and notable discussions on various topics.

### **Pre-processing the Data:**
The initial phase of the project involved **data pre-processing**, where the manually tagged tweets were transformed into an appropriate format for training the NER model. The data was pre-processed into the **IOB format** (Inside, Outside, Beginning), a standard format used in sequence labeling tasks. In IOB tagging:
- **B (Beginning)** marks the first token of an entity.
- **I (Inside)** marks tokens that are part of an entity.
- **O (Outside)** marks tokens that do not belong to any entity.

This format allows the model to correctly recognize the boundaries and labels of entities in a sequence of words, crucial for the NER task.

### **BERT Transformer Model:**
The core of the NER system was a pre-trained **BERT (Bidirectional Encoder Representations from Transformers)** model, a powerful language representation model that captures the context of words in a sentence by considering both the left and right context. BERT has been highly successful in a range of NLP tasks due to its pre-training on large text corpora and its ability to fine-tune on specific tasks like NER.

In this project, BERT was fine-tuned for sequence labeling by integrating a **sequence labeling head**. The sequence labeling head is a layer added on top of the pre-trained BERT model, which helps the model classify each token in the input sequence as one of the predefined entity types (NORP, PERSON, LOC, etc.).

### **Inference Strategy Comparison:**
The model’s performance was evaluated using two different inference strategies:

1. **Majority Voting**: This approach involves predicting the entity type based on the majority vote of all the tokens in a span. For example, if three tokens in a sequence are classified as "PERSON" and one token as "O," the span (e.g., a person’s name) will be classified as "PERSON" based on the majority vote.

2. **First Tag Span**: In this method, the first tag encountered in the token sequence is used as the label for the entire span. For instance, if the first token of a name is tagged as "PERSON," the entire span (the name) will be labeled as "PERSON," regardless of subsequent tokens' tags.

These strategies were compared to evaluate their effectiveness in improving the accuracy of entity recognition and ensuring the proper labeling of multi-token entities.

### **Performance Evaluation:**
The comparison between **majority voting** and **first tag span strategy** provided insights into which inference method produced the best results for the given dataset. In particular, the evaluation focused on:
- **Accuracy**: How well the model identifies and classifies entities correctly.
- **Entity Boundary Recognition**: How accurately the model determines where each entity starts and ends.
- **False Positives/Negatives**: The rate at which incorrect entities were identified or real entities were missed.

By testing both strategies, the project aimed to determine which method yields the best trade-off between precision and recall for the NER task, especially in the noisy, informal language of tweets.

### **Challenges and Considerations:**
- **Informal Language**: Tweets often include slang, abbreviations, and emojis, which can make entity recognition more challenging.
- **Contextual Ambiguity**: Social media posts often contain ambiguous references, and the same word could refer to different types of entities depending on context. For example, "Apple" could refer to a fruit or a company, and the model needs to distinguish between these meanings.
- **Data Imbalance**: Some entity types may be underrepresented in the dataset, leading to challenges in accurately identifying those entities.

### **Conclusion:**
The project demonstrated the ability of the BERT model to successfully perform Named Entity Recognition on tweets, which is crucial for extracting meaningful information from large volumes of social media content. By fine-tuning BERT and experimenting with different inference strategies, it was possible to enhance the accuracy of entity classification, ultimately contributing to better insights into public discussions and trends on platforms like X (formerly Twitter). 

This method can be applied in a variety of contexts such as sentiment analysis, trend monitoring, and social media analytics, where identifying and understanding key entities in user-generated content is essential. Further improvements can be made by refining the model with larger datasets, exploring additional entity types, and optimizing the pre-processing pipeline for specific social media content characteristics.
