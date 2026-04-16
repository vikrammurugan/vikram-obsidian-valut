## Transformer
> Transformer is an attention-based deep learning architecture that processes tokens in parallel and captures contextual relationships using self-attention, making it the foundation of modern LLMs.
--- 

## tradintional vs new machine learning ?
Traditional ML is feature-driven and task-specific, whereas LLM-based ML is data-driven, transformer-based, and capable of learning generalized language intelligence.

----

## what is prompt
A prompt is the text input or instruction provided to an LLM that guides the model on what task to perform and how to generate the response.

---

## what is context window
Context window is the maximum number of input and output tokens an LLM can process in a single interaction, acting as the model’s temporary working memory.

---

## RNN
RNN is a neural network architecture designed for sequential data that uses hidden states to retain information from previous time steps, enabling it to model temporal dependencies.

---

## RNN vs Transformer
|Topic|RNN|Transformer|
|---|---|---|
|Processing|Sequential|Parallel|
|Memory|Hidden state|Self-attention|
|Long dependencies|Weak|Strong|
|Training speed|Slow|Fast|
|Parallel GPU usage|Poor|Excellent|
|Context understanding|Limited|Excellent|
|Used in LLMs|Rare|Standard|
|Scaling|Hard|Easy|
RNN models sequential dependencies through recurrent hidden states, while transformers use self-attention to process all tokens in parallel, making transformers faster, more scalable, and better for long-context understanding.


---
## encoder and decoder
In transformers, the encoder converts input tokens into contextual representations, while the decoder uses those representations along with previously generated tokens to produce the output sequence.

---

## token
A token is the smallest unit of text processed by an LLM, which may represent a word, subword, punctuation, or symbol, and is converted into token IDs before model inference.

---

## tokenizer
A tokenizer is a preprocessing component that splits raw text into tokens and maps them into numerical token IDs that can be understood by the LLM.

---
## transformer diagram
![[Pasted image 20260416074637.png]]

---
## embadding
Embedding converts text into meaning-preserving vectors.

---

## vector
A vector in LLM is a high-dimensional numerical representation of text semantics, used internally for embeddings, attention computation, and similarity search.

---
## position embadding
Positional embedding is an additional vector added to token embeddings to encode token order information so transformers can understand sequence structure.

---
# token embadding

Token embedding is the process of converting each token ID into a dense semantic vector using a learnable embedding matrix before passing it into transformer layers.

---

## token vs position embadding
|Topic|Token Embedding|Positional Embedding|
|---|---|---|
|Purpose|Meaning|Order|
|Input|Token ID|Token position|
|Learns|Semantic similarity|Sequence location|
|Example|loan ≈ credit|pos1, pos2, pos3|
|Needed For|Meaning understanding|Sentence structure|
Token embedding tells _what_, positional embedding tells _where_.

