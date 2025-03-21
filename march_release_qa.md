### Unsharded

|Model|export|compile|server|Server Test|
|---|---|---|---|---|
|`Llama-3.1-8B`|PASS|PASS|PASS|input getting repeated as o/p
|`Llama-3.1-8B-Instruct`|PASS|PASS|PASS|PASS
|`Llama-3.1-70B`|
|`Llama-3.1-70B-Instruct`
| `Llama-3.1-405b`
|`Llama-3.1-405b-Instruct`
|`Mistral-Nemo-Base-2407`
|`Mistral-Nemo-Instruct-2407



### Sharded : TP8

|Model|export|compile|server|Server Test|
|---|---|---|---|---|
|`Llama-3.1-8B`|PASS|PASS|PASS|input getting repeated as o/p
|`Llama-3.1-8B-Instruct`|PASS|PASS|PASS|PASS
|`Llama-3.1-70B`|
|`Llama-3.1-70B-Instruct`
| `Llama-3.1-405b`
|`Llama-3.1-405b-Instruct`
|`Mistral-Nemo-Base-2407`
|`Mistral-Nemo-Instruct-2407


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


4> with flux1.dev, I am seeing error as
```
ERROR: Building 'Fetch https://sharkpublic.blob.core.windows.net/sharkpublic/flux.1/weights/exported_parameters_bf16/flux_dev_sampler_bf16.irpa' failed:
    Traceback (most recent call last):
      File "/home/dhirajp/march_25/.venv/lib/python3.11/site-packages/iree/build/executor.py", line 416, in invoke
        self._invoke()
      File "/home/dhirajp/march_25/.venv/lib/python3.11/site-packages/shortfin_apps/utils.py", line 222, in _invoke
        self._invoke(retries=retries)
      File "/home/dhirajp/march_25/.venv/lib/python3.11/site-packages/shortfin_apps/utils.py", line 222, in _invoke
        self._invoke(retries=retries)
      File "/home/dhirajp/march_25/.venv/lib/python3.11/site-packages/shortfin_apps/utils.py", line 222, in _invoke
        self._invoke(retries=retries)
      [Previous line repeated 1 more time]
      File "/home/dhirajp/march_25/.venv/lib/python3.11/site-packages/shortfin_apps/utils.py", line 224, in _invoke
        raise IOError(f"Failed to fetch URL '{self.url}': {e}") from None
    OSError: Failed to fetch URL '.../exported_parameters_bf16/flux_dev_sampler_bf16.irpa': HTTP Error 404: The specified blob does not exist.
```

5> For any model, when trying with sharded version, getting error during compile time
```
./my_model/mistral_nemo_base_tp8.mlir:3:1: error: failed to solve for affinity analysis
module @module {
^
./my_model/mistral_nemo_base_tp8.mlir:3:1: note: see current operation: 
"builtin.module"() <{sym_name = "module"}> ({
```

