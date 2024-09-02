# ConvNeXt V2
ConvNext which modernized from Convnets could also be scalable architectures, but when testing we still use benchmarking supervised learning performance on Imagenet.

Many architectures has been shifting from supervised learning with labels to self-supervised pre-training, such as MAE which built from VIT architecture.

MAE's arch is not suitable for Convnets cause its encode-decoder design is optimized for transformers. VIT focus on patches when Convnets is sliding windows.

## ConvNeXt v2

Make a mask-based self-supervised learning for Convnet models.

*sparse convolutions

*replace transformer with convnext block

*global response normalization layer
# LLaMA：Open and Efficient Foundation Language Models

Previous assumption: more parameters lead to better performance. 

[scaling laws](https://arxiv.org/abs/2203.15556): best performances is achieved by smaller models training on more data.

LLaMA: inference is important, which scaling laws discarded.

Scaling laws recommends training 10B model on 200B tokens,  but finded that 7B model is enough.

## Pre-training data

CommonCrawl, C4, Github, Wiki, Books, ArXiv, StackExchange

tools: 

[CCNet pipline](https://arxiv.org/abs/1911.00359): deduplicates data, performs language identification with
a fastText linear classifier to remove non-English pages and filters low quality content with an n-gram language model.(what is n-gram language model?)

trained a linear model to classify pages used as references.

Tokenizer: tokenize the data with byte-pair encoding(BPE) algorithm, using implementation from Sentence-Piece. 

## Architecture

1. Based on Transformer.

2. Pre-normalization from GPT-3: normalize the input of each transformer sub-layer, instead of normalizing the output.

3. SwiGLU activation function from PaLM: replace ReLU by SwiGLU activation function.

4. Rotary Embeddings from GPTNeo: remove the absolute positional embeddings, add RoPE.

## Build-up from Scratch

### tokenizer：

SentencePiece(Byte-Pair Encoding algorithm): runs on UTF-8 encoded strings. First used in GPT-2.

3 functions of tokenizer:

1: train tokenizer vocabulary and merges on a given text.

2: encode from text to tokens

3: decode from tokens to text

basic tokenizer class: train, encode, decode
