# Custom Paraphrase Generator (CPG)
Comparison between a custom parapharse generator and LLM

For building CPG a hugging face pretrained model - [ramsrigouthamg/t5-large-paraphraser-diverse-high-quality](https://huggingface.co/ramsrigouthamg/t5-large-paraphraser-diverse-high-quality) was used. Mistral's "mistral-large-latest" was used as the llm model through API.

## Development of CPG:
For the paraphrasing task, t5 based model was utilised. These models suffer through limitation of token input limit and low context span. To overcome this, the input context was split into sentences and each sentence was passed separately for paraphrasing. This method was found effective as compared to sending whole conetxt together. Also using this method the required threshild of 80% input tokens has been met, which was not possible as in case of sending the whole context at once. On the other hand this approach has increased latency.

## Evaluation metric
As the aim of parapharsing is to make input more readable in simple language, [Flesch reading ease](https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests). The output should have more readability as compared to the input i.e. higher Flesch score. Along with that, ROUGE and BLUE metrics are used to gauge the text generation. Model latency has been captured in the Tokens/Second. All results are avaialble in `results` folder.

## Conclusion
The CPG has found to be performing better on all evaluation metrics with a cost of high latency.
