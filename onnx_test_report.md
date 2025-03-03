### CPU and GPU report for failing models

### common failures : 

| model | stage | error | issue no | 
|---|---|---|---|
|maxvit_xlarge_tf_512.in21k_ft_in1k|setup|INVALID_PROTOBUF||
|migraphx_sd__unet__model|import|Assertion `g.get() != nullptr` failed: Warning: onnx version converter is unable to parse input model||
|migraphx_sdxl__unet__model|import| Assertion `version >= version_range.first && version <= version_range.second` failed: Warning: invalid version||
|resnest50d_1s4x24d_vaiq | compilation |'memref.copy' op write affecting operations on global resources are restricted to workgroup distributed contexts | https://github.com/iree-org/iree/issues/19760 |
|sequencer2d_l|compilation| Fail to legalize : ONNX.LSTM|https://github.com/nod-ai/SHARK-ModelDev/issues/947|
|KeypointRCNN_vaiq_int8|compilation| Fail to legalize : ONNX.IF||
|retinanet_resnet50_fpn_vaiq_int8|compilation| 'tensor.dim' op unexpected during shape cleanup; dynamic dimensions must have been resolved prior to leaving the flow dialect||
|migraphx_bert__bertsquad-12|compilation|expected type to be 'tensor<?x?x?xf32>' or a rank-reduced version. (size mismatch)||
|migraphx_onnx-model-zoo__gpt2-10|compilation|'hal.tensor.barrier' op failed to verify that all of {sources, results} have same type||

### CPU only : NONE

### GPU only : 14

| model | stage | error | issue no | CPU status|
|---|---|---|---|---|
|model--finetuned_gpt2-large_sst2_negation0.2--yuhuizhang|setup|zipfile.BadZipFile: File is not a zip file|| PASS|
|model--long-t5-tglobal-large-pubmed-3k-booksum-16384-WIP14--pszemraj,model--long-t5-tglobal-large-pubmed-3k-booksum-16384-WIP13--pszemraj,model--long-t5-tglobal-base-16384-book-summary--pszemraj,model--long-t5-tglobal-large-pubmed-3k-booksum-16384-WIP17--pszemraj,model--long-t5-tglobal-base-16384-booksum-V11-big_patent-V2--pszemraj,model--long-t5-tglobal-large-pubmed-3k-booksum-16384-WIP--pszemraj,model--long-t5-tglobal-base-16384-booksum-V12--pszemraj,model--tglobal-large-booksum-WIP4-r1--pszemraj,model--long-t5-tglobal-large-pubmed-3k-booksum-16384-WIP15--pszemraj,model--s2t-medium-librispeech-asr--facebook|compilation|'arith.extui' op operand type 'i64' and result type 'i32' are cast incompatible | https://github.com/iree-org/iree/issues/19179|| PASS|
|lambda_resnet50ts, lambda_resnet26t|compilation|'linalg.generic' op inferred inpuoutput operand #2 has shape's dimension #1 to be 32, but found 16||PASS|
|RDN_pytorch_vaiq_int8|compilation|'func.func' op uses 606208 bytes of shared memory; exceeded the limit of 65536 bytes||Numerics|
