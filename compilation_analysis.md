### current status of compilation failures





crash: 3 : https://github.com/iree-org/iree/issues/18927
===
model--long-t5-tglobal-base-16384-book-summary--pszemraj
model--long-t5-tglobal-base-16384-booksum-V11-big_patent-V2--pszemraj
migraphx_bert__bertsquad-12




failed to legalize unresolved materialization from ('i64') to 'index' that remained live after conversion:1 https://github.com/iree-org/iree/issues/18899
===
model--long-t5-tglobal-base-16384-booksum-V12--pszemraj


'torch.prim.If' op  along control flow edge from Region #0 to parent results: 4
===
model--splinter-large-few-shot-k-16-finetuned-squad-seed-0--anas-awadalla
model--splinter-large-few-shot-k-16-finetuned-squad-seed-2--anas-awadalla
model--splinter-large-few-shot-k-16-finetuned-squad-seed-4--anas-awadalla
model--splinter-large-few-shot-k-32-finetuned-squad-seed-2--anas-awadalla
KeypointRCNN_vaiq_int8
retinanet_resnet50_fpn_vaiq_int8


vm.div.i64.u' op is a divide by constant zero : 3
===
swinv2_cr_small_224.sw_in1k
swinv2_cr_small_ns_224.sw_in1k
swinv2_cr_tiny_ns_224.sw_in1k




'tensor.reshape' op source and destination tensor should have the same number of elements: 1
==
bat_resnext26ts.ch_in1k

'func.func' op exceeded stack allocation limit of 32768 bytes for function. Got 1048576 bytes: 2
===
model--s2t-medium-librispeech-asr--facebook
migraphx_models__whisper-tiny-encoder

failed to legalize operation 'torch.aten.convolution' that was explicitly marked illegal: 1
===
model--squeezebert-uncased-finetuned-squad--SupriyaArun




'vector.shape_cast' op source/result number of elements must match: 1
==
LRASPP_vaiq_int8

One or more operations with large vector sizes (8192 bytes) were found: 1
===
U-2-Net_vaiq_int8

'tensor.dim' op unexpected during shape cleanup; dynamic dimensions must have been resolved prior to leaving the flow dialect: 1
==
migraphx_agentmodel__AgentModel

type of return operand 0 ('!torch.vtensor<[?,384],f32>') doesn't match function result type ('!torch.vtensor<[1,384],f32>') in function @torch-jit-export: 1
==
migraphx_bert__bert-large-uncased

failed to legalize operation 'torch.aten.nonzero': 1
==
migraphx_onnx-model-zoo__gpt2-10


onnx.LSTM: 1
===
sequencer2d_l


crash during runtime: 93 : https://github.com/iree-org/iree/issues/18929
====
model--125M_GPTneo_reward_base--Myashka
model--CodeGen-350M-Multi--xhyi
model--GPyT--Sentdex
model--Jasmine-350M--UBC-NLP
model--PT_GPTNEO125_ATG--xhyi
model--TinyStories-1Layer-21M--roneneldan
model--TinyStories-1M--roneneldan
model--TinyStories-2Layers-33M--roneneldan
model--TinyStories-33M--roneneldan
model--TinyStories-3M--roneneldan
model--TinyStories-8M--roneneldan
model--cm_code_clippy--ncoop57
model--codegen-350M-mono--Salesforce
model--codegen-350M-mono-4bit-qlora--iamtarun
model--distilgpt2-sd--aabidk
model--distilgpt2-stable-diffusion--FredZhang7
model--distilgpt2-stable-diffusion-v2--FredZhang7
model--distilgpt2-wikitext2--Intel
model--finetuned-opt-squad-dataset--choohan
model--finetuned-opt-squad-dataset-2--choohan
model--finetuned-opt-squad-dataset-3--choohan
model--finetuned_distilgpt2_sst2_negation0.0001_pretrainedTrue_epochs1--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.001_pretrainedTrue_epochs1--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.001_pretrainedTrue_epochs3--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.01_pretrainedFalse_epochs10--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.01_pretrainedFalse_epochs3--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.01_pretrainedFalse_epochs6--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.01_pretrainedTrue_epochs1--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.0_pretrainedFalse_epochs0--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.0_pretrainedTrue--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.0_pretrainedTrue_epochs0--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.1_pretrainedFalse_epochs10--jhaochenz
model--finetuned_distilgpt2_sst2_negation0.1_pretrainedTrue_epochs1--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.0001_pretrainedTrue--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.0001_pretrainedTrue_epochs1--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.0001_pretrainedTrue_epochs3--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.0005_pretrainedTrue--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.001_pretrainedTrue_epochs1--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.001_pretrainedTrue_epochs3--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.01--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.01_pretrainedFalse_epochs10--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.01_pretrainedFalse_epochs3--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.01_pretrainedTrue_epochs1--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.05--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.05_pretrainedFalse--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.0_pretrainedFalse--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.0_pretrainedFalse_epochs30--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.1_pretrainedFalse_epochs10--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.1_pretrainedTrue_epochs1--jhaochenz
model--finetuned_gpt2-medium_sst2_negation0.2--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.2_pretrainedFalse--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.5--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.5_pretrainedFalse--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.8--yuhuizhang
model--finetuned_gpt2-medium_sst2_negation0.8_pretrainedFalse--yuhuizhang
model--finetuned_gpt2_sst2_negation0.0001_pretrainedFalse_epochs1--yuhuizhang
model--finetuned_gpt2_sst2_negation0.0001_pretrainedTrue--yuhuizhang
model--finetuned_gpt2_sst2_negation0.0005_pretrainedTrue--yuhuizhang
model--finetuned_gpt2_sst2_negation0.001_pretrainedTrue--yuhuizhang
model--finetuned_gpt2_sst2_negation0.05--yuhuizhang
model--finetuned_gpt2_sst2_negation0.0_pretrainedFalse--yuhuizhang
model--finetuned_gpt2_sst2_negation0.2_pretrainedFalse--yuhuizhang
model--finetuned_gpt2_sst2_negation0.5--yuhuizhang
model--finetuned_gpt2_sst2_negation0.8--yuhuizhang
model--finetuned_gpt2_sst2_negation0.8_pretrainedFalse--yuhuizhang
model--finetuning-sentiment-model-3000-samples--DravenTay
ecaresnet269d
model--gpt2--openai-community
model--gpt2-650k-stable-diffusion-prompt-generator--Ar4ikov
model--gpt2-alpaca-gpt4--vicgalle
model--gpt2-finetuning-sentiment-model-3000-samples--LYTinn
model--gpt2-imdb-sentiment-classifier--mnoukhov
model--gpt2-wikitext103--himanshubeniwal
model--gpt2_wikitext37_7k_pretrained_iphone_1e4--himanshubeniwal
model--hebrew_poetry-gpt_neo-small--Norod78
model--ia-detection-tiny-random-gptj--arincon
model--megatron-gpt2-345m--robowaifudev
model--my_awesome_gptj_model--anandshende
model--neo-125m-wills-loss-function-by-tr--Jellywibble
model--opt-125m-finetuned-squad-assignment--Isente
model--opt-350m--facebook
model--opt-350m-wikitext2--lnair
model--opt-finetuned-squad-dataset--choohan
model--ov-gpt2-fp32-kv-cache--vuiseng9
model--ov-opt-350m-8bit-85pc-sparse-kv-cache--vuiseng9
model--ov-opt-350m-8bit-kv-cache--vuiseng9
model--ov-opt-350m-fp32-kv-cache--vuiseng9
model--tiny-random-GPTJForQuestionAnswering--hf-tiny-model-private
model--tiny-random-GPTNeoForSequenceClassification--hf-tiny-model-private
model--tiny-random-gptj-for-sequence-classification--ydshieh
model--wikitext-ds--mahmoudNG
migraphx_ORT__distilgpt2_1
migraphx_ORT__onnx_models__distilgpt2_1_fp16_gpu

