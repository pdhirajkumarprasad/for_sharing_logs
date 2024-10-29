### current status of compilation failures

operand #0 does not dominate this use: 9 https://github.com/iree-org/iree/issues/18879
===
hrnet_w18_small_v2_vaiq
hrnet_w18_small_vaiq
hrnet_w18_vaiq
hrnet_w30_vaiq
hrnet_w32_vaiq
hrnet_w40_vaiq
hrnet_w44_vaiq
hrnet_w48_vaiq
hrnet_w64_vaiq

onnx.Resize: 11 https://github.com/nod-ai/SHARK-ModelDev/issues/599
===
crossvit_15_240
crossvit_15_dagger_240
crossvit_15_dagger_408
crossvit_18_240
crossvit_18_dagger_240
crossvit_18_dagger_408
crossvit_9_240
crossvit_9_dagger_240
crossvit_base_240
crossvit_small_240
crossvit_tiny_240

crash: 3 : https://github.com/iree-org/iree/issues/18927
===
model--long-t5-tglobal-base-16384-book-summary--pszemraj
model--long-t5-tglobal-base-16384-booksum-V11-big_patent-V2--pszemraj
migraphx_bert__bertsquad-12

'stream.async.slice' op has invalid Read access range [0 to 8 for 8] of resource %0 with size 0; length > resource size : 74 https://github.com/iree-org/iree/issues/18926
==
tf_efficientnet_b0.aa_in1k
efficientnet_b3_pruned.in1k
tf_efficientnet_b0.ap_in1k
tf_efficientnet_b0.ns_jft_in1k
tf_efficientnet_b1.aa_in1k
tf_efficientnet_b1.ap_in1k
tf_efficientnet_b1.ns_jft_in1k
tf_efficientnet_b2.aa_in1k
tf_efficientnet_b2.ap_in1k
tf_efficientnet_b2.ns_jft_in1k
tf_efficientnet_b3.aa_in1k
tf_efficientnet_b3.ap_in1k
tf_efficientnet_b3.ns_jft_in1k
tf_efficientnet_b4.aa_in1k
tf_efficientnet_b4.ap_in1k
tf_efficientnet_b4.ns_jft_in1k
tf_efficientnet_b5.ap_in1k
tf_efficientnet_b5.ns_jft_in1k
tf_efficientnet_b5.ra_in1k
tf_efficientnet_b6.aa_in1k
tf_efficientnet_b6.ap_in1k
tf_efficientnet_b6.ns_jft_in1k
tf_efficientnet_b7.ap_in1k
tf_efficientnet_b7.ns_jft_in1k
tf_efficientnet_b7.ra_in1k
botnet26t_256
tf_efficientnet_b8.ap_in1k
tf_efficientnet_b8.ra_in1k
tf_efficientnet_l2.ns_jft_in1k
tf_efficientnet_l2.ns_jft_in1k_475
tf_efficientnetv2_l.in1k
tf_efficientnetv2_l.in21k_ft_in1k
tf_efficientnetv2_m.in1k
coat_lite_mini
coat_lite_small
tf_efficientnetv2_m.in21k_ft_in1k
coat_lite_tiny
tf_efficientnetv2_s.in1k
tf_efficientnetv2_s.in21k_ft_in1k
tf_efficientnetv2_xl.in21k_ft_in1k
tf_mixnet_l.in1k
tf_mixnet_m.in1k
tf_mixnet_s.in1k
tf_mobilenetv3_large_075.in1k
tf_mobilenetv3_large_100.in1k
maxvit_base_tf_224.in1k
maxvit_base_tf_384.in1k
maxvit_base_tf_384.in21k_ft_in1k
maxvit_base_tf_512.in1k
maxvit_base_tf_512.in21k_ft_in1k
maxvit_large_tf_224.in1k
maxvit_large_tf_384.in1k
maxvit_large_tf_384.in21k_ft_in1k
maxvit_large_tf_512.in1k
maxvit_large_tf_512.in21k_ft_in1k
maxvit_small_tf_224.in1k
maxvit_small_tf_384.in1k
maxvit_small_tf_512.in1k
maxvit_tiny_tf_224.in1k
maxvit_tiny_tf_384.in1k
maxvit_tiny_tf_512.in1k
maxvit_xlarge_tf_384.in21k_ft_in1k
maxvit_xlarge_tf_512.in21k_ft_in1k
nasnetalarge
pnasnet5large
davit_base.msft_in1k
davit_small.msft_in1k
davit_tiny.msft_in1k
vit_relpos_base_patch16_clsgap_224.sw_in1k
vit_relpos_medium_patch16_cls_224.sw_in1k
sebotnet33ts_256
eca_botnext26ts_256
efficientnet_b1_pruned.in1k
efficientnet_b2_pruned.in1k


failed to legalize operation 'torch.aten.__or__.bool' : 6 https://github.com/nod-ai/SHARK-ModelDev/issues/873
==
twins_svt_base
twins_svt_large
twins_svt_small
jx_nest_base
jx_nest_small
jx_nest_tiny


failed to legalize unresolved materialization from ('i64') to 'index' that remained live after conversion:1
===
model--long-t5-tglobal-base-16384-booksum-V12--pszemraj


'torch.prim.If' op  along control flow edge from Region #0 to parent results: 4
===
model--splinter-large-few-shot-k-16-finetuned-squad-seed-0--anas-awadalla
model--splinter-large-few-shot-k-16-finetuned-squad-seed-2--anas-awadalla
model--splinter-large-few-shot-k-16-finetuned-squad-seed-4--anas-awadalla
model--splinter-large-few-shot-k-32-finetuned-squad-seed-2--anas-awadalla


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


failed to legalize operation onnx.if: 1
===
KeypointRCNN_vaiq_int8
retinanet_resnet50_fpn_vaiq_int8


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
