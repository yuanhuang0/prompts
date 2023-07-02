# Articles
- GPT best practices https://platform.openai.com/docs/guides/gpt-best-practices
- A Blog in Chinese about the article above https://mp.weixin.qq.com/s/u72wzup-5DCQrJdNNYJwDA

## Strategy 1: Write clear instructions

### 1.1 Include details in your query to get more relevant answers
```
Worse: Summarize the meeting notes.
Better: Summarize the meeting notes in a single paragraph. Then write a markdown list of the speakers and each of their key points. Finally, list the next steps or action items suggested by the speakers, if any.
```

### 1.2 Ask the model to adopt a persona
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

### 1.3 Use delimiters to clearly indicate distinct parts of the input
```
SYSTEM You will be provided with a pair of articles (delimited with XML tags) about the same topic. First summarize the arguments of each article. Then indicate which of them makes a better argument and explain why.
USER <article> insert first article here </article> <article> insert second article here </article>
```

### 1.4 Specify the steps required to complete a task
```
SYSTEM Use the following step-by-step instructions to respond to user inputs.
Step 1 - The user will provide you with text in triple quotes. Summarize this text in one sentence with a prefix that says "Summary: ".
Step 2 - Translate the summary from Step 1 into Spanish, with a prefix that says "Translation: ".
```
 
### 1.5 Provide examples
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

### 1.6 Specify the desired length of the output
```
Summarize the text delimited by triple quotes in about 50 words. """insert text here"""
Summarize the text delimited by triple quotes in 2 paragraphs. """insert text here"""
Summarize the text delimited by triple quotes in 3 bullet points. """insert text here"""
```

## Strategy 2: Provide reference text

### 2.1 Instruct the model to answer using a reference text
*For GPT API:*
```
SYSTEM Use the provided articles delimited by triple quotes to answer questions. If the answer cannot be found in the articles, write "I could not find an answer."

USER
"""
The Baltimore Police Department is investigating a mass shooting in which 30 people were gunned down at a block party in the US city of Baltimore.  

Key points:
The mass shooting took place during a block party in South Baltimore
The Baltimore Mayor described the incident as a "reckless, cowardly act"
Police are reviewing the "extensive" crime scene to identify the suspects
Acting Commissioner Richard Worley said police received "numerous calls" about a shooting in the 800 block of Greta Avenue just after 12:30am local time.

He said 30 people were shot, three of which are in a critical condition and two are dead.

"This is an extensive crime scene, our detectives are going to be here quite a while," he said.

The 28 people who were injured have been taken to hospitals around the region.

The Acting Commissioner said the two people who died were both adults. 

He said the mass shooting took place during a "block party" in the Brooklyn Homes area of South Baltimore.
"""

Question:  Were the injured people taken to hospitals far away from the region?

// GPT API replied:
No, the people who were injured in the mass shooting were taken to hospitals around the region.
```
