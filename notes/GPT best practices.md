# Articles
- GPT best practices https://platform.openai.com/docs/guides/gpt-best-practices
- A Blog in Chinese about the article above https://mp.weixin.qq.com/s/u72wzup-5DCQrJdNNYJwDA

## Tactics:

### Include details in your query to get more relevant answers
```
Worse: Summarize the meeting notes.
Better: Summarize the meeting notes in a single paragraph. Then write a markdown list of the speakers and each of their key points. Finally, list the next steps or action items suggested by the speakers, if any.
```

### Ask the model to adopt a persona
*For GPT API:*
```
SYSTEM When I ask for help to write something, you will reply with a document that contains at least one joke or playful comment in every paragraph.
USER Write a thank you note to my steel bolt vendor for getting the delivery in on time and in short notice. This made it possible for us to deliver an important order.
```

*For ChatGPT:*
```
When I ask for help to write something, you will reply with a document that contains at least one joke or playful comment in every paragraph.
----------
Write a thank you note to my steel bolt vendor for getting the delivery in on time and in short notice. This made it possible for us to deliver an important order.
```

### Use delimiters to clearly indicate distinct parts of the input
```
SYSTEM You will be provided with a pair of articles (delimited with XML tags) about the same topic. First summarize the arguments of each article. Then indicate which of them makes a better argument and explain why.
USER <article> insert first article here </article> <article> insert second article here </article>
```

### Specify the steps required to complete a task
```
SYSTEM Use the following step-by-step instructions to respond to user inputs.
Step 1 - The user will provide you with text in triple quotes. Summarize this text in one sentence with a prefix that says "Summary: ".
Step 2 - Translate the summary from Step 1 into Spanish, with a prefix that says "Translation: ".
```
 
### Provide examples
*For GPT API:*
```
SYSTEM Answer in a consistent style.
USER Teach me about patience.
ASSISTANT The river that carves the deepest valley flows from a modest spring; the grandest symphony originates from a single note; the most intricate tapestry begins with a solitary thread.
USER Teach me about GPT.

// GPT API replied:
ASSISTANT Born from the matrix of algorithms and a wealth of data, GPT, or Generative Pretraining Transformer, is an AI model from OpenAI. It learns from a myriad of phrases, sentences, and structures, refining its knowledge and understanding. Serving as a tapestry of information, it weaves together relevant responses, much like an intricate symphony composed from a chorus of individual notes. From understanding human language to generating creative content, GPT is an embodiment of the boundless potential present within the realm of artificial intelligence.
```

*For ChatGPT:*
```
Answer in a consistent style, following the example:
Q: Teach me about patience.
A:  The river that carves the deepest valley flows from a modest spring; the grandest symphony originates from a single note; the most intricate tapestry begins with a solitary thread.
Q: Teach me about GPT.
A: 

// ChatGPT replied:
A: The mightiest intellect of AI emerges from a simple algorithm; the richest tapestry of language grows from a singular neural net; the most profound comprehension springs from a single byte of data.
``` 

### Specify the desired length of the output
