----------------------Pre-Launch-----------------------------------------\

uv pip install -e acestep/third_parts/nano-vllm

--<--<output: Resolved 30 packages in 553ms
      Built nano-vllm @ file:///F:/AceStep/ACE-Step-1.5/acestep/thi
Prepared 1 package in 1.49s
Uninstalled 2 packages in 110ms
Installed 2 packages in 3.94s
 - flash-attn==2.8.2 (from https://github.com/sdbds/flash-attention-for-windows/releases/download/2.8.2/flash_attn-2.8.2+cu128torch2.7.1cxx11abiFALSEfullbackward-cp311-cp311-win_amd64.whl)
 + flash-attn==2.8.2+cu128torch2.7.1cxx11abifalsefullbackward (from https://github.com/sdbds/flash-attention-for-windows/releases/download/2.8.2/flash_attn-2.8.2+cu128torch2.7.1cxx11abiFALSEfullbackward-cp311-cp311-win_amd64.whl)
 ~ nano-vllm==0.2.0 (from file:///F:/AceStep/ACE-Step-1.5/acestep/third_parts/nano-vllm)\
 
 Notes: there is a logic when the app first starts to sync these libraries, it is by the original coders design. Somewhere in the sync code nano-vllm gets lost sometimes. If you plan on using it in the lora train workflow, make sure you run the uv pip ... command above before starting the app. I does not affect the music generation workflow and the same workflow can work without it from what I see. You will see it Uninstalled and Installed 2 packages after starting the acestep app:\

When acestep starts:
(ace-step) PS c:\AceStep\ACE-Step-1.5> uv run .\acestep
Uninstalled 2 packages in 73ms
Installed 2 packages in 4.08s
Loaded configuration from c:\AceStep\ACE-Step-1.5\.env\

 ---------------------------Launch--------------------------------\
 
 uv run .\acestep
 
 CPU offload disabled by default (GPU >= 16GB)
usage: acestep [-h] [--port PORT] [--share] [--debug]
               [--server-name SERVER_NAME]
               [--language {en,zh,ja}]
               [--service_mode SERVICE_MODE]
               [--init_service INIT_SERVICE]
               [--checkpoint CHECKPOINT]
               [--config_path CONFIG_PATH]
               [--device {auto,cuda,cpu,xpu}]
               [--init_llm INIT_LLM]
               [--lm_model_path LM_MODEL_PATH]
               [--backend {vllm,pt}]
               [--use_flash_attention USE_FLASH_ATTENTION]
               [--offload_to_cpu OFFLOAD_TO_CPU]
               [--offload_dit_to_cpu OFFLOAD_DIT_TO_CPU]
               [--enable-api] [--auth-username AUTH_USERNAME]
               [--auth-password AUTH_PASSWORD]
               [--api-key API_KEY]
               
--------------------------Workflow-------------------------------\

Simple:
Generate Song description->Create Sample->Generate->STOP (this clears the tensors in memory and the temp files in C:\Users\user0\AppData\Local\Temp\*)

If you do not use STOP, the Gradio Interface will hang.
Refreshing the browser will unhang the interface but will revert all settings to default.
You do not need to ReInitialize after a browser refresh!

The back end is solid, I suggest using a 3rd party interface like the fspecii UI.
https://github.com/fspecii/ace-step-ui
