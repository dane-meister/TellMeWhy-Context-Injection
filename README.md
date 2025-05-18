# TellMeWhy-Context-Injection
 ## Original Source
 Our project is based on a paper/project linked below. We used their dataset and trained our models from the HuggingFace transformers API.
 [Original Paper where the Idea came from](https://aclanthology.org/2022.emnlp-main.79/)
 [Original Git Project where the Idea came from](https://github.com/StonyBrookNLP/knowwhy)
[Data used from that project](https://huggingface.co/datasets/StonyBrookNLP/tellmewhy)


 ## Modified Files
 We ended up not reusing any files from the original paper. We did modify their dataset however:
 [Data used from that project](https://huggingface.co/datasets/StonyBrookNLP/tellmewhy) 
 

## How to Train and Test our Models
We used a Google Colab Notebook that can be run sequentially on a GPU instance to train, save, and evaluate our models. Without a GPU instance the notebook will crash as in some places we move tensors to the GPU explicitly. The notebook requires access to the runner's google drive, and will open a folder named "CSE_354_project", or create it if it doesn't exist. Preprocessing the data requires loading the JSON named "*ALL_CONTEXT_DATA_1.json*" that we created and linked in the data section below.
[Link to Notebook](https://colab.research.google.com/drive/1OD20QNgY24b6lUG22S8CK1lcuuheJw_N?usp=sharing)

Additionally inside the notebook we link to our context generation using Gemini that we did over the course of days due do Gemini's API limits. To run this notebook successfully you need to add a Google Gemini API key in the secrets section of Colab.

## Our Models and Data
[Drive link to our no context tuned model](https://drive.google.com/drive/folders/1jmfPBUO8D9ErSxLEyizCAHfwYmCZsZPi?usp=sharing)
[Drive link to our context tuned model](https://drive.google.com/drive/folders/1-5-wsyQgdH7D9G9WtVD3Udr09FqwllPW?usp=sharing)
[Drive link to our modified data in JSON format](https://drive.google.com/file/d/1yfivuLQud6rmaVqtAW3mtTR2PIL8oIZ6/view?usp=drive_link)
[Drive link to folder containing all files above](https://drive.google.com/drive/folders/1MQjohFNC19qhgc5hetsw9g9yr6bheoF2?usp=sharing)

## Prompts used
Prompt we had given to gemini for context injection:
```py
prompt = '''Given the following narrative sentences that describe a story, produce a sequence of concise and to the point sentences that bring in commonsense information, and external world knowledge that is relevant. Be very verbose about commonsense knowledge and explain the reason why things are done.

  

Here is an example:

narrative: Cam ordered a pizza and took it home. He opened the box to take out a slice. Cam discovered that the store did not cut the pizza for him. He looked for his pizza cutter but did not find it. He had to use his chef knife to cut a slice.

Pizza is a food. People eat food when they are hungry. Pizza is usually already cut. Cam got the pizza from the store.

  

Produce context sentences to the following narrative without any formatting, just as a sequence of 4 short, simple, and single clause sentences, do NOT reason through multiple sentences, each sentence should state commonsense information related to the narrative:

{narrative}

'''
```
Prompt format we trained our models on, either:
```py
f"Narrative: {narrative} Question: {question}"
```
or
```py
f"Narrative: {narrative} Context: {context} Question: {question}"
```

## Requirements
All requirements are set to be installed in the notebook before, or when they are needed. The notebook works if run sequentially.