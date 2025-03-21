### Sglang-shortfin
### Version used

```
iree-base-compiler 3.3.0rc20250320
iree-base-runtime  3.3.0rc20250320
iree-tools-tf      20250320.1206
iree-tools-tflite  20250320.1206
iree-turbine       3.3.0rc20250320
sharktank          3.3.0rc20250320
shortfin           3.3.0rc20250320
```

### Unsharded

|Model|export|compile|server|Server Test|
|---|---|---|---|---|
|`Llama-3.1-8B`|PASS|PASS|PASS|input getting repeated as o/p
|`Llama-3.1-8B-Instruct`|PASS|PASS|PASS|PASS
|`Llama-3.1-70B`|PASS|PASS|PASS|Dumping empty or dumping extra unrelated text
|`Llama-3.1-70B-Instruct`|PASS|PASS|PASS|PASS
| `Llama-3.1-405b`
|`Llama-3.1-405b-Instruct`|
|`Mistral-Nemo-Base-2407`|PASS|PASS|PASS|Washington, D.C.begin_of_text Name the capital of the United States. Washington, D.C. Name the capital of the United States.
|`Mistral-Nemo-Instruct-2407|PASS|PASS|PASS|PASS



### Sharded : TP8

|Model|export|compile|server|Server Test|
|---|---|---|---|---|
|`Llama-3.1-8B`|PASS|PASS|PASS|input getting repeated as o/p
|`Llama-3.1-8B-Instruct`|PASS|PASS|PASS|PASS
|`Llama-3.1-70B`|PASS|PASS|PASS|Dumping empty or dumping extra unrelated text
|`Llama-3.1-70B-Instruct`|PASS|PASS|PASS|PASS
| `Llama-3.1-405b`
|`Llama-3.1-405b-Instruct`
|`Mistral-Nemo-Base-2407`|PASS|PASS|PASS|Washington, D.C.begin_of_text Name the capital of the United States. Washington, D.C. Name the capital of the United States.
|`Mistral-Nemo-Instruct-2407|PASS|PASS|PASS|PASS



Following steps mentioned here for nightly

https://github.com/nod-ai/shark-ai/blob/main/docs/shortfin/llm/user/llama_serving.md

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
but it works fine if I use cli for downloading.

On serving side, on 1st run, it's giving empty o/p and then garbage value on restart


### Shortfin

1> We need to install PIL (pillow), pytest

2> We need to use sharktank/shortfin of `0321` build else recent change are not visible

3> We need to run from '/shortfin/' else it will error out at https://github.com/nod-ai/shark-ai/tree/main/shortfin/python/shortfin_apps/flux#start-flux-server
 ```
  File "/home/dhirajp/march_25/shortfin/flux/dev/shark-ai/shortfin/python/shortfin_apps/flux/components/config_struct.py", line 106, in load_json
    with open(path, "rt") as f:
         ^^^^^^^^^^^^^^^^
FileNotFoundError: [Errno 2] No such file or directory: 'python/shortfin_apps/flux/examples/flux_dev_config_mixed.json'
```

4> Should be add detail about port like https://github.com/nod-ai/shark-ai/blob/main/docs/shortfin/llm/user/llama_serving.md#3-run-the-shortfin-llm-server ?

5> 


