## Adding a model to a serving endpoint Databricks.

### Ensure Your Model is Registered.
- The first thing you will have to do is to download an open source model.
- We going to use a open source model called "BAAI/bge-base-en-v1.5" 
[[here](https://huggingface.co/BAAI/bge-base-en-v1.)]
- To download the model we do it using python code (*if there is another easier way at the time of making this PoC I had not found it*). 

**Before you run the code you need to have a few things installed**

  - OpenSSL, In my experience do not install the latest version [[here](https://slproweb.com/products/Win32OpenSSL.html)]
  - Pytorch (the configuraiton need to be created according you machine) and thenn add it to requirements.txt [[here](https://pytorch.org/get-started/locally/#windows-anaconda)]

In my opinion the best thing to do is to create a python enviroment because if you are using the latest version of python there might not be modules for that version yet, for my example I am using python 3.9. and from there install the `requirements.txt`. 

Enviroment

```python
conda create --name myenv python=3.9
conda activate myenv
```

Download model

```python
from transformers import AutoModel, AutoTokenizer

# Define the model name
model_name = "BAAI/bge-base-en-v1.5"

# Download the model and tokenizer
model = AutoModel.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)

# Save the model and tokenizer to a directory
model_save_path = "./baai_bge_base_en_v1_5"
tokenizer_save_path = "./baai_bge_base_en_v1_5"

model.save_pretrained(model_save_path)
tokenizer.save_pretrained(tokenizer_save_path)

print(f"Model and tokenizer have been saved to {model_save_path}")

```