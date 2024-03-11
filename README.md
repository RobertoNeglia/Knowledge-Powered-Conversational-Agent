# Knowledge-Powered-Conversational-Agent
A ChatBot that uses the WizardOfWikipedia dataset to answer with context.

# Dataset
The dataset consists of open-domain dialog containing utterances that were generated from content extracted from Wikipedia articles. Multiple candidate Wikipedia passages are associated with each turn in the dialog, where one of them is considered the  reference” (i.e. correct) passage and was used to generate the response text.

# How it's used
At each turn, after the user input, the ChatBot chooses the correct passage from Wikipedia from a candidate set of passages, and then uses it to generate a response in the dialog using the information contained in the reference passage retrieved.
The bot is based on a GPT-2 model and it is then fine-tuned using the WizardOfWikipedia dataset. To retrieve the passages, a [SBERT pre-trained model](https://huggingface.co/sentence-transformers/multi-qa-MiniLM-L6-cos-v1) is used to perform a semantic search in the space of passages. Finally, another [SBERT pre-trained Cross-Encoder model](https://huggingface.co/cross-encoder/ms-marco-MiniLM-L-6-v2) is used to re-rank the retrieved passages.
The ChatBot response is then converted to audio using a Text-To-Speech model.
