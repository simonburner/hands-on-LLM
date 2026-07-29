# Chapter 9: Multimodal Large Language Models

## Key takeaways

### Transformers for Vision

The Vision Transformer (ViT) uses transformer architecture for computer vision. Specifically, it's used to transform an image into representations that can be used for a variety of tasks (classification, clustering,...).

Instead of splitting up text into tokens, ViT converts an image into patches of that image.

<img width="589" height="196" alt="Screenshot 2026-07-29 at 19 53 33" src="https://github.com/user-attachments/assets/c286f9ae-1d41-4319-aef8-aa8bc50f2a13" />

However, we cannot just assign each patch with an ID as we do with word tokens, as these patches won't likely appear in other images. Instead, the patches are linearly embedded to create numerical representations, which can then be used as the input of a Transformer.

<img width="593" height="500" alt="Screenshot 2026-07-29 at 20 01 53" src="https://github.com/user-attachments/assets/e3979231-cb0b-4600-965f-57af849c92ff" />

### Multimodal Embedding Models

<img width="593" height="299" alt="Screenshot 2026-07-29 at 20 04 02" src="https://github.com/user-attachments/assets/057946a8-46a5-44f0-b11d-1ff0fd189731" />

An advantage to multimodal embedding models is that it allows to compare multimodal representations (text, images), since the resulting embeddings coexist in the same vector space:

<img width="589" height="389" alt="Screenshot 2026-07-29 at 20 06 38" src="https://github.com/user-attachments/assets/d7265200-db58-4d38-a127-769cc9195997" />

The most well-known and most-used multimodal embedding model is Contrastive Language-Image Pre-training **(CLIP)**:

- As the resulting embeddings lie in the same vector space, embeddings of images and text can be compared. CLIP is usable for:
  - Zero-shot classification: we can compare the embedding of an image with an embedding of the description of classes to find what class is most similar.
  - Clustering: cluster both images and a keywords to find which keywords belong to which sets of images.
  - Search: across millions of texts or images, we can find what relates to an input text or image.
  - Generation: text-to-image guidance.
 
- How CLIP models are trained:

  <img width="586" height="346" alt="Screenshot 2026-07-29 at 20 29 28" src="https://github.com/user-attachments/assets/1f9522c7-8b93-4467-b447-618c41ded589" />
  &nbsp;
  <img width="585" height="730" alt="Screenshot 2026-07-29 at 20 29 42" src="https://github.com/user-attachments/assets/6d4a5573-3917-49f1-b16c-0e3f6d2d385d" />

### Making Text Generation Models Multimodal

Text generation are great at reasoning about textual information and responding with natural language, however they're limited to the domain they were trained on, namely text. As a result to this, attempts to introduce a form of multimodality to existing models have been made. One of the resulting methods is BLIP-2, which is an easy-to-use and modular system that allows adding vision capabilities to existing language models.

#### BLIP-2

Instead of building an entire multimodal model architecture from scratch, BLIP-2 bridges the vision-language gap by using the Querying Transformer (Q-Former), which connects a pre-trained image encoder and a pre-trained LLM.

<img width="585" height="191" alt="Screenshot 2026-07-29 at 21 47 37" src="https://github.com/user-attachments/assets/27464658-2a0c-497a-a1cc-7cdd0c59f0e0" />

This way, BLIP-2 only needs to train the Q-Former module. To connect the two pre-trained models, Q-Former mimics the architectures of the other two models. It has two modules that share their attention layers:

- An Image Transformer to interact with the Vision Transformer
- A Text Transformer to interact with the LLM

The Q-Former is trained in two stages:

- In step 1, image-caption pairs are used to train the Q-Former so it can represent both image and text. The images are passed to the ViT to extract the image embeddings, these embeddings are the input of the Q-Former's ViT module. The captions are used as the input of the Q-Former's Text Transformer module.

  <img width="586" height="272" alt="Screenshot 2026-07-29 at 21 57 12" src="https://github.com/user-attachments/assets/072812c3-adc1-4d85-ab45-fd7ceae8cae3" />

  With these training inputs, the Q-Former is then trained on the following three tasks:

  - Image-text contrastive learning: align pairs of image and text so they maximize their mutual information.
  - Image-text matching: a classification task which predicts if an image and text pair is matched (positive) and unmatched (negative).
  - Image-grounded text generation: trains the model to generate based on an input image.

    <img width="586" height="337" alt="Screenshot 2026-07-29 at 22 05 06" src="https://github.com/user-attachments/assets/45b1b68b-d9e3-4d35-9e34-b39bc1374e6c" />

- In step 2, the learned embeddings now contain visual information in the same dimensional space as the corresponding textual information. These learned embeddings are then passed to the LLM.

  <img width="587" height="237" alt="Screenshot 2026-07-29 at 22 08 56" src="https://github.com/user-attachments/assets/896eec49-98e3-4e05-994a-81d4441e4c4a" />

The full BLIP-2 procedure:

<img width="559" height="340" alt="Screenshot 2026-07-29 at 22 10 22" src="https://github.com/user-attachments/assets/581ce7b0-e34a-4813-8a96-689a78283e73" />






