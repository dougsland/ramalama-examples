# ramalama-examples
Just examples of usage.

Deepseek

```console
ramalama run deepseek-r1:8b
> What's deepseek?
```

Granite-code from IBM, specific for writing source code, 3B params model, not the smartest at this time.

```console
ramalama run granite-code:3b
> How to write a hello world in python?
```

TinyLama

```console
ramalama run tinyllama:latest
```

[Moondream](https://github.com/vikhyat/moondream)

```console
ramalama run moondream:latest
```

huggingface
```console
ramalama run huggingface://afrideva/Tiny-Vicuna-1B-GGUF/tiny-vicuna-1b.q2_k.gguf
```

Configuring Hugging Face as the default transport:
You can also set Hugging Face as the default transport for RamaLama by setting an environment variable:
```console
export RAMALAMA_TRANSPORT=huggingface
```
After setting this, you can pull models using their short names if defined in a shortnames.conf file, or directly by their Hugging Face repository and model name without needing the huggingface:// prefix for every command.

