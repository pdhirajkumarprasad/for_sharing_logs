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


