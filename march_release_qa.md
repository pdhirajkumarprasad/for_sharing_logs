1>	This should be pulled before shark-ai[app] installation so that it become valid when someone is trying nightly
```
# Fast installation of torch with just CPU support.
pip install torch --index-url https://download.pytorch.org/whl/cpu "torch>=2.3.0,<2.6.0"
```

2>	For nightly, we need pip install dataclasses_json 

3> if I use script like
```
from transformers import AutoModel, AutoModelForSequenceClassification, AutoTokenizer

model_name = "mistralai/Mistral-Nemo-Instruct-2407"
model = AutoModel.from_pretrained(model_name)
model.save_pretrained('./saved_model')

tokenizer = AutoTokenizer.from_pretrained(model_name)
tokenizer.save_pretrained('./saved_model')
```

and 

```
export WEIGHTS_DIR=/path/to/safetensors/weights_directory/
git clone --depth 1 https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
python3 convert_hf_to_gguf.py $WEIGHTS_DIR --outtype f16 --outfile $EXPORT_DIR/<output_gguf_name>.gguf
```

getting error as
```
INFO:hf-to-gguf:Loading model: my_model
ERROR:hf-to-gguf:Model MistralModel is not supported
```
but it works file if I use cli


## Status
- Sglang-shortfin run fp16 models

|model| TP| status
|---|---|---|
|Llama-3.1-8B-Instruct| tp-1 | PASS
|Llama-3.1-8B-Instruct| tp-8 | Failed during iree-compile : error: failed to solve for affinity analysis


