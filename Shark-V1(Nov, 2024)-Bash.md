### I followed the steps mentioned in [user_guide](https://github.com/nod-ai/SHARK-Platform/blob/main/docs/user_guide.md) and using python 3.12


## Installation
- We need following pip install command added in setup for server/client to work
   - pip install uvicorn
   - pip install fastapi
   - pip install aiohttp

## ease of use

- When we are running server on a port, which is already in use, along with error, we are dumping lot's of nonbind message. It will be better if we can hide/disable them

```
  2024-11-14 20:40:56 - INFO - Application startup complete.
2024-11-14 20:40:56 - ERROR - [Errno 98] error while attempting to bind on address ('0.0.0.0', 8000): [errno 98] address already in use
2024-11-14 20:40:56 - INFO - Waiting for application shutdown.
INFO:root:Shutting down service 'sd'
[2024-11-14 20:40:56.569] [info] [manager.py:40] Shutting down system manager
2024-11-14 20:40:56 - INFO - Application shutdown complete.
INFO:root:System manager command processor stopped
nanobind: leaked 128 instances!
 - leaked instance 0x7ff5273365c8 of type "_shortfin_default.lib.local.Program"
 - leaked instance 0x7ff573f40f48 of type "_shortfin_default.lib.local.ProgramFunction"
 - leaked instance 0x7ff5a5b17188 of type "_shortfin_default.lib.local.ProgramFunction"
 - leaked instance 0x7ff5a5b30148 of type "_shortfin_default.lib.local.StaticProgramParameters"
 - leaked instance 0x7ff573f417c8 of type "_shortfin_default.lib.local.ProgramFunction"
 - leaked instance 0x7ff5273368f8 of type "_shortfin_default.lib.local.Program"
 - leaked instance 0x7ff5a5b20848 of type "_shortfin_default.lib.local.ProgramFunction"
 - leaked instance 0x7ff5273369e8 of type "_shortfin_default.lib.local.Program"
 - leaked instance 0x7ff573f41288 of type "_shortfin_default.lib.local.ProgramFunction"
 - leaked instance 0x7ff573f40b08 of type "_shortfin_default.lib.local.ProgramFunction"
 - leaked instance 0x8e33730 of type "_shortfin_default.lib.local.Fiber"
 - leaked instance 0x7ff527336a48 of type "_shortfin_default.lib.local.Program"
 - leaked instance 0x7ff573f40a88 of type "_shortfin_default.lib.local.ProgramFunction"
```

#### different options on client side

- for outputdir, when I am providing 'abc' it creates and saves image into that directory but if I am providing 'abc/xyz', it's erroring out saying no such directory. Should not we create directory and save the image?
- In interactive mode, we don't have clean way to exit. Better to add that. Currently we can do with 'Ctrl+C' but it's like hard exit


### different options on server side
- Following help option should be removed from user_guide

```
  --root-path ROOT_PATH
```

- Following help option is missing from user_guide

```
  --tuning_spec TUNING_SPEC
                        Path to transform dialect spec if compiling an executable with tunings.
  --topology {spx_single,cpx_single,spx_multi,cpx_multi}
                        Use one of four known performant preconfigured device/fiber topologies.
  --use_tuned USE_TUNED
                        Use tunings for attention and matmul ops. 0 to disable.
```

- when device is 'local-task', getting below error. Is that expected?

```
[2024-11-14 22:24:59.950] [info] [service.py:135] Loading inference program: clip, worker index: 0, device: [Device(name='hostcpu:0:0@0', ordinal=0:0, node_affinity=5, capabilities=0x1)]
[2024-11-14 22:24:59.950] [info] [manager.py:40] Shutting down system manager
INFO:root:System manager command processor stopped
2024-11-14 22:25:00 - ERROR - Traceback (most recent call last):
  File "/temp_dir_by_dhiraj/gitRepo/SHARK-Platform/.venv/lib/python3.12/site-packages/starlette/routing.py", line 693, in lifespan
    async with self.lifespan_context(app) as maybe_state:
               ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/contextlib.py", line 210, in __aenter__
    return await anext(self.gen)
           ^^^^^^^^^^^^^^^^^^^^^
  File "/temp_dir_by_dhiraj/gitRepo/SHARK-Platform/.venv/lib/python3.12/site-packages/shortfin_apps/sd/server.py", line 51, in lifespan
    service.start()
  File "/temp_dir_by_dhiraj/gitRepo/SHARK-Platform/.venv/lib/python3.12/site-packages/shortfin_apps/sd/components/service.py", line 138, in start
    self.inference_programs[worker_idx][component] = sf.Program(
                                                     ^^^^^^^^^^^
ValueError: <vm>:0: INCOMPATIBLE; HAL device `__device_0` not found or unavailable: #hal.device.target<"hip", [#hal.executable.target<"rocm", "rocm-hsaco-fb", {abi = "hip", iree.gpu.target = #iree_gpu.target<arch = "gfx942", features = "", wgp = <compute =  fp64|fp32|fp16|int64|int32|int16|int8, storage =  b64|b32|b16|b8, subgroup =  shuffle|arithmetic, dot =  dp4xi8toi32, mma = [<MFMA_F32_16x16x4_F32>, <MFMA_F32_16x16x16_F16>, <MFMA_F32_32x32x8_F16>, <MFMA_F32_16x16x16_BF16>, <MFMA_F32_32x32x8_BF16>, <MFMA_F32_16x16x32_F8E4M3FNUZ>, <MFMA_F32_16x16x32_F8E5M2FNUZ>, <MFMA_I32_16x16x32_I8>, <MFMA_I32_32x32x16_I8>], subgroup_size_choices = [64], max_workgroup_sizes = [1024, 1024, 1024], max_thread_count_per_workgroup = 1024, max_workgroup_memory_bytes = 65536, max_workgroup_counts = [2147483647, 2147483647, 2147483647], max_load_instruction_bits = 128, simds_per_wgp = 4, vgpr_space_bits = 16384>>, ukernels = "none"}>]>; 
```

- Impact of option like 'worker_per_device/fiber_per_device' not clear as I don't see any ipact of this. Even it takes '-1/0' value .
- with --artifact_flag or even without, it's wiating for 3/4 minutes after this. why?

```
Servicing 3 outstanding tasks
Completed BuildEntrypoint(path='sdxl')
Servicing 2 outstanding tasks
Completed Compiling BuildFile[gen](sdxl/stable_diffusion_xl_base_1_0_clip_bs1_64_fp16.mlir) (for amdgpu-gfx942)
Servicing 1 outstanding tasks
Completed BuildFile[bin](sdxl/stable_diffusion_xl_base_1_0_clip_bs1_64_fp16_amdgpu-gfx942.vmfb)
Servicing 5 outstanding tasks
Completed BuildFile[gen](sdxl/stable_diffusion_xl_base_1_0_punet_dataset_i8.irpa)
Completed BuildFile[gen](sdxl/stable_diffusion_xl_base_1_0_punet_bs1_64_1024x1024_i8.mlir)
Scheduling action: Compiling BuildFile[gen](sdxl/stable_diffusion_xl_base_1_0_punet_bs1_64_1024x1024_i8.mlir) (for amdgpu-gfx942)
Servicing 3 outstanding tasks
Completed BuildEntrypoint(path='sdxl')
```  
 
