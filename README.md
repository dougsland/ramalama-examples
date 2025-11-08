# ramalama-examples
Just examples of usage.

---

## Table of Contents
1. [Overview](#overview)  
2. [Running Deepseek](#running-deepseek)  
3. [Running Granite-code (IBM)](#running-granite-code-ibm)  
4. [Running TinyLama](#running-tinyllama)  
5. [Running Moondream](#running-moondream)  
6. [Running Tiny-Vicuna](#running-tiny-vicuna)  
7. [Configuring Hugging Face as the Default Transport](#configuring-hugging-face-as-the-default-transport)  
8. [Installing Hugging Face CLI](#installing-hugging-face-cli)
9. [Logging using official huggingface cli](logging-using-official-huggingface-clie)


**Running Deepseek**

```console
ramalama run deepseek-r1:8b
> What's deepseek?
```

**Running Granite-code** from IBM, specific for writing source code, 3B params model, not the smartest at this time.

```console
ramalama run granite-code:3b
> How to write a hello world in python?
```

**Running TinyLama**

```console
ramalama run tinyllama:latest
```

**Running Moondream**
[Moondream](https://github.com/vikhyat/moondream)

```console
ramalama run moondream:latest
```

**Running Tiny-Vicuna**
```console
ramalama run huggingface://afrideva/Tiny-Vicuna-1B-GGUF/tiny-vicuna-1b.q2_k.gguf
```

**Configuring Hugging Face as the default transport**
You can also set Hugging Face as the default transport for RamaLama by setting an environment variable:
```console
export RAMALAMA_TRANSPORT=huggingface
```
After setting this, you can pull models using their short names if defined in a shortnames.conf file, or directly by their Hugging Face repository and model name without needing the huggingface:// prefix for every command.

**Installing huggingface CLI**
```
pip install -U "huggingface_hub[cli]"
```

**Logging using official huggingface cli**
```
source ~/.bashrc
huggingface-cli login --token "$HUGGING_FACE_HUB_TOKEN"
huggingface-cli whoami
dougsland
```
