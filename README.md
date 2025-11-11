# ramalama-examples
Just examples of usage.

---
# 📘 Table of Contents

- [Running Deepseek](#running-deepseek)
- [Running Granite code from IBM](#running-granite-code-from-ibm)
- [Running TinylLama](#running-tinyllama)
- [Running Mistral](#running-mistral)
- [Running Moondream](#running-moondream)
- [Running Tiny-Vicuna](#running-tiny-vicuna)
- [Configuring Hugging Face as the Default Transport](#configuring-hugging-face-as-the-default-transport)
- [Installing Hugging Face CLI](#installing-hugging-face-cli)
- [Logging Using Official Hugging Face CLI](#logging-using-official-hugging-face-cli)
- [QuickStart: Hugging Face Python and Client](#quickstart-hugging-face-python-and-client)
- [List Models](#list-models)
- [Delete Model](#delete-model)
- [Analyzing an Image](#analyzing-an-image)
- [Upgrade via pip](#upgrade-via-pip)
- [Fix applehv gpu](#fix-applehv-gpu)
- [Updating Podman via brew](#updating-podman-via-brew)
  
## Running Deepseek

```console
ramalama run deepseek-r1:8b
> What's deepseek?
```

## Running Granite code from IBM

```console
ramalama run granite-code:3b
> How to write a hello world in python?
```

## Running TinylLama

```console
ramalama run tinyllama:latest
```

## Running Mistral

```console
$ ramalama run mistral
Downloading hf://lmstudio-community/Mistral-7B-Instruct-v0.3-GGUF/Mistral-7B-Instruct-v0.3-Q4_K_M.gguf ...
Trying to pull hf://lmstudio-community/Mistral-7B-Instruct-v0.3-GGUF/Mistral-7B-Instruct-v0.3-Q4_K_M.gguf ...
Downloading Mistral-7B-Instruct-v0.3-Q4_K_M.gguf
```

## Running Moondream
[Moondream](https://github.com/vikhyat/moondream)

```console
ramalama run moondream:latest
```

## Running Tiny-Vicuna
```console
ramalama run huggingface://afrideva/Tiny-Vicuna-1B-GGUF/tiny-vicuna-1b.q2_k.gguf
```

## Configuring Hugging Face as the default transport
You can also set Hugging Face as the default transport for RamaLama by setting an environment variable:
```console
export RAMALAMA_TRANSPORT=huggingface
```
After setting this, you can pull models using their short names if defined in a shortnames.conf file, or directly by their Hugging Face repository and model name without needing the huggingface:// prefix for every command.

## Installing Hugging Face CLI
```console
pip install -U "huggingface_hub[cli]"
```

## Logging Using Official Hugging Face CLI
```
source ~/.bashrc
huggingface-cli login --token "$HUGGING_FACE_HUB_TOKEN"
huggingface-cli whoami
dougsland
```

## QuickStart: Hugging Face Python and Client  
https://huggingface.co/docs/huggingface_hub/en/quick-start

## List Models

```bash
ramalama list
NAME                                                                             MODIFIED     SIZE
ollama://tinyllama/tinyllama:latest                                              55 years ago 0 B
ollama://granite3.2/granite3.2:latest                                            6 months ago 4.6 GB
ollama://llama2/llama2:latest                                                    6 months ago 3.56 GB
ollama://library/granite4:tiny-h                                                 1 week ago   3.94 GB
ollama://library/granite3.1-dense:latest                                         1 week ago   4.65 GB
hf://TheBloke/Mistral-7B-Instruct-v0.2-GGUF/mistral-7b-instruct-v0.2.Q4_K_M.gguf 6 months ago 4.07 GB
hf://TheBloke/TinyLlama-1.1B-Chat-v1.0-GGUF                                      3 hours ago  460.74 MB
hf://HuggingFaceTB/smollm-135M-instruct-v0.2-Q8_0-GGUF                           1 week ago   138.1 MB
https://huggingface.co/deepseek-ai/DeepSeek-OCR                                  4 days ago   129.92 KB
```

## Delete model

```bash
$ ramalama rm ollama://tinyllama/tinyllama:latest
```

## Analyzing an image

To be determined
```bash
cd /image/location
$ ramalama run llava:7b
Downloading ollama://library/llava:7b ...
Trying to pull ollama://library/llava:7b ...
$ what is in this image ./Lion.jpg
```

## Upgrade via pip
```console
pip install --upgrade ramalama
```

## Fix applehv gpu 
```
Warning! Your VM podman-machine-default is using applehv, which does not support GPU. Only the provider libkrun has GPU support. See man ramalama-macos for more information. Do you want to proceed without GPU? (yes/no): ??
```

```console
brew tap slp/krunkit
brew install krunkit
$ podman machine rm podman-machine-default -f
$ CONTAINERS_MACHINE_PROVIDER='libkrun' podman machine init --now  
```

## Updating podman via brew

```console
brew update
brew upgrade podman
```

## ramalama serve

```console
ramalama serve --port 8081 tinyllama
```

In another terminal:

To execute a question:
```console
curl -X POST http://localhost:8080/v1/completions \
  -H "Content-Type: application/json" \
  -d '{
        "model": "your_model_name",
        "prompt": "Hello, how are you?",
        "max_tokens": 50,
        "temperature": 0.7
      }'
```

For health:
```
curl -X GET http://127.0.0.1:8081/health
{"status":"ok"}
```

For props:
```
curl -X GET http://127.0.0.1:8081/props
{"default_generation_settings":{"params":{"seed":4294967295,"temperature":0.800000011920929,"dynatemp_range":0.0,"dynatemp_exponent":1.0,"top_k":40,"top_p":0.949999988079071,"min_p":0.05000000074505806,"top_n_sigma":-1.0,"xtc_probability":0.0,"xtc_threshold":0.10000000149011612,"typical_p":1.0,"repeat_last_n":64,"repeat_penalty":1.0,"presence_penalty":0.0,"frequency_penalty":0.0,"dry_multiplier":0.0,"dry_base":1.75,"dry_allowed_length":2,"dry_penalty_last_n":4096,"mirostat":0,"mirostat_tau":5.0,"mirostat_eta":0.10000000149011612,"max_tokens":-1,"n_predict":-1,"n_keep":0,"n_discard":0,"ignore_eos":false,"stream":true,"n_probs":0,"min_keep":0,"chat_format":"Content-only","reasoning_format":"none","reasoning_in_content":false,"thinking_forced_open":false,"samplers":["penalties","dry","top_n_sigma","top_k","typ_p","top_p","min_p","xtc","temperature"],"speculative.n_max":16,"speculative.n_min":0,"speculative.p_min":0.75,"timings_per_token":false,"post_sampling_probs":false,"lora":[]},"n_ctx":4096},"total_slots":1,"model_path":"/mnt/models/tinyllama-1.1b-chat-v1.0.Q2_K.gguf","modalities":{"vision":false,"audio":false},"endpoint_slots":true,"endpoint_props":false,"endpoint_metrics":false,"webui":true,"chat_template":"{% for message in messages %}\n{% if message['role'] == 'user' %}\n{{ '<|user|>\n' + message['content'] + eos_token }}\n{% elif message['role'] == 'system' %}\n{{ '<|system|>\n' + message['content'] + eos_token }}\n{% elif message['role'] == 'assistant' %}\n{{ '<|assistant|>\n'  + message['content'] + eos_token }}\n{% endif %}\n{% if loop.last and add_generation_prompt %}\n{{ '<|assistant|>' }}\n{% endif %}\n{% endfor %}","bos_token":"<s>","eos_token":"</s>","build_info":"b1-b5
```

Chat completion endpoint
```
curl -X POST http://localhost:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
        "model": "your_model_name",
        "messages": [
          { "role": "system", "content": "You are a helpful assistant." },
          { "role": "user",   "content": "What is 2 + 2?" }
        ],
        "max_tokens": 20,
        "temperature": 0.5
      }'
```

JSON format

```
curl -X POST http://127.0.0.1:8081/v1/completions \
  -H "Content-Type: application/json" \
  -d '{
        "model": "your_model_name",
        "prompt": "Hello, how are you?",
        "max_tokens": 50,
        "temperature": 0.7,
        "format": "json"
      }'
```
