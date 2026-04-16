A transformer is a model that **understands relationships between words (tokens) using attention**.

Instead of reading text one word at a time like older RNNs, it looks at **all words in parallel** and decides:

> “Which previous words are important for predicting the next word?”

That is why LLMs generate coherent text.
### examples
> **The animal didn’t cross the road because _it_ was tired**

Transformer uses **self-attention** to understand that **“it” = animal**, not road.

This ability to connect distant words is why transformers are powerful

## mutli headed mechanism
The **multi-headed mechanism** in transformers is called **Multi-Head Attention (MHA)**.

It means the model uses **multiple attention “heads” in parallel**, where each head learns a **different type of relationship between words/tokens**.

> [!Simply] 
> Instead of having **one brain looking at the sentence**, transformer uses **many small brains at the same time**.


## self-attention mechanism
each word looks at every other word in the same sentence and decides which ones are important.
>**The animal didn’t cross the road because _it_ was tired**

## RNN
An **RNN (Recurrent Neural Network)** is an older type of neural network designed to **process sequence data one step at a time**.  
It was widely used before transformers for:

- text generation
- speech recognition
- time series
- translation

> [!NOTE] Title
> It remembers the **previous word / previous time step** and uses that memory for the current prediction.


