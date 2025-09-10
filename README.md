# 🚀 Transformers
This repository (and LinkedIn series) is about breaking down Transformers—the deep learning models behind almost every major NLP breakthrough today.

We’ll start simple: what Transformers are, why they matter, and how they work step by step.

## 📌 1. What & Why Transformers?

Imagine you’re using Google Translate:
```
English → Spanish
"Hello, how are you?" → "Hola, ¿cómo estás?"
```

Old models might’ve output:
> “Hola, cómo eres tú?” ❌ (Literal, awkward)

Transformers get the **intent** — because they **pay attention**.

### 📌 Encoder-Decoder Architecture 
Transformers are built around an **encoder-decoder** structure:

- **Encoder**: Reads the input sentence and creates a representation.
- **Decoder**: Takes that representation and generates the output sentence. 

**Problem with older encoder-decoder models (like RNNs/LSTMs):**
- As sentence length increases, they struggle.
- Translation quality drops, often measured by the **BLEU score** (a metric for translation accuracy).
Example:

```
English: "The quick brown fox jumps over the lazy dog near the river."
Spanish (bad translation): "El rápido marrón zorro salta sobre perro
perezoso."
```

### 📌 Attention Mechanism  

Here’s the fix: **attention**.  

Instead of only relying on the last hidden state of the encoder, attention lets the decoder look back at *all* input words and decide which ones matter most when generating each output word.

Example (English → Spanish):

```
Input: "I love eating apples."
When predicting "me gusta comer manzanas",
- The model attends to "love" when generating "me gusta"
- Then to "eating" for "comer"
- Then to "apples" for "manzanas"
```

So the translation is context-aware.

### 📌 Self-Attention (The Transformer Superpower)  

Regular attention works word by word. Transformers go further: they use **self-attention**, meaning:  

- Every word in a sentence looks at every other word, *in parallel*.  
- This allows scaling—because instead of processing words one after another, Transformers handle them all at once.  

Example:  

Sentence: *"The animal didn’t cross the street because it was too tired."*  

Which word does *“it”* refer to?  
- Self-attention helps the model figure out that *“it”* links back to *“the animal”*, not *“the street”*. 

### 📌 Contextual Embeddings  

Unlike older word embeddings (like Word2Vec) that gave one static vector per word, Transformers create **contextual embeddings**.  

Example:  

```
Word: "bank"
Sentence 1: "I deposited money in the bank."
Sentence 2: "The fisherman sat by the river bank."
```

Old models → same embedding for “bank.”  
Transformers → different embeddings depending on context.  