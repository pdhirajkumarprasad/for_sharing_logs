## Testing strategy

- Running multiple server on same machine with different port
- Should not downloand artifacts when path is provided

## shortfin_apps.sd.server with different options:


| Flags | options |Verification Owner|Issues|
|---|---|---|---|
|--host HOST |
|--port PORT |
|--root-path ROOT_PATH |
|--timeout-keep-alive |
|--device | local-task,hip,amdgpu |
|--target | gfx942,gfx1100 |
|--device_ids |
|--tokenizers |
|--model_config |
| --workers_per_device | 
| --fibers_per_device |
| --isolation |	per_fiber, per_call, none |
| --show_progress  |
| --trace_execution | 
| --amdgpu_async_allocations |
| --splat   |
| --build_preference | compile,precompiled |
| --compile_flags |
| --flagfile FLAGFILE |  
| --artifacts_dir ARTIFACTS_DIR |



## shortfin_apps.sd.server with different options:

| Flags | Verification Owner|Issues||
|---|---|---|---|
|--file|
|--reps|
|--save|
|--outputdir|
|--steps|
|--interactive|
