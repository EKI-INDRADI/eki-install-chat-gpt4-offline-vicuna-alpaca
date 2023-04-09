
![BENCHMARK](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/chart.svg)

NOTE :

CHAT-GPT SUPPORT SEMUA BAHASA, BLOCK NEGATIVE QUESTION/ANSWER

VICUNA SUPPORT BAHASA INDONESIA, TRAINING MODEL 92% nya CHAT-GPT, SEMI UNCENSSORED QUESTION/ANSWER JIKA MENGGUNAKAN CHARACTER EVAI

ALPACA HANYA BAHASA INGGRIS, TRAINING MODEL 76% nya CHAT-GPT, SUPPORT UNCENSSORED QUESTION/ANSWER JIKA MENGGUNAKAN CHARACTER EVAI

<details>
  <summary>MODEL : VICUNA, ALPACA (CLICK)</summary>

![MODEL](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/MODEL.png)

</details>


<details>
  <summary>RESOURCE (CLICK)</summary>

![RESOURCE](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/RESOURCE.png)

</details>

<details>
  <summary>ENABLE API (CLICK)</summary>

![API](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/obabooga_api.png)

</details>


<details>
  <summary>ALBEDO PERSONALITY + CHARACTER RESPONSE</summary>

![ALBEDO](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/ALBEDO_PROFILE.png)

![ALBEDO](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/ALBEDO.png)

</details>


<details>
  <summary>EVAI PERSONALITY + CHARACTER RESPONSE</summary>


![EVAI](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/EVAI_PROFILE.png)

![EVAI](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/EVAI_1.png)

![EVAI](https://github.com/EKI-INDRADI/eki-install-chat-gpt4-offline-vicuna-alpaca/blob/main/EVAI_2.png)


</details>



---


0.1 download Oobabooga Webui zip : https://github.com/oobabooga/text-generation-webui/releases/download/installers/oobabooga-windows.zip

0.2 unzip 

1.1 install.bat choose A (CUDA)

1.2 download-model.bat choose A



---

```sh
cd (DIR)\oobabooga-windows\text-generation-webui\models
```
(karena menggunakan hunggingface maka file size sebaiknya download manual)

```sh
git lfs install
GIT_LFS_SKIP_SMUDGE=1
git clone https://huggingface.co/anon8231489123/gpt4-x-alpaca-13b-native-4bit-128g 
git clone https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g
```

```sh
download manual https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g/gpt-x-alpaca-13b-native-4bit-128g-cuda.pt 
save (DIR)\oobabooga-windows\text-generation-webui\models\gpt4-x-alpaca-13b-native-4bit-128g\gpt-x-alpaca-13b-native-4bit-128g-cuda.pt 
```

```sh
download manual https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g/vicuna-13b-4bit-128g.safetensors
save (DIR)\oobabooga-windows\text-generation-webui\models\vicuna-13b-GPTQ-4bit-128g\vicuna-13b-4bit-128g.safetensors
```

```sh
after clone 
delete 
.git
.gitattributes
ggml_README.txt
pytorch_model.bin.index.json
README.md
trainer_state.json
training_args.bin
```

1.3 create/edit file start-webui.bat


start-webui.bat (choose model)
```sh
@echo off

@echo Starting the web UI...

cd /D "%~dp0"

set MAMBA_ROOT_PREFIX=%cd%\installer_files\mamba
set INSTALL_ENV_DIR=%cd%\installer_files\env

if not exist "%MAMBA_ROOT_PREFIX%\condabin\micromamba.bat" (
  call "%MAMBA_ROOT_PREFIX%\micromamba.exe" shell hook >nul 2>&1
)
call "%MAMBA_ROOT_PREFIX%\condabin\micromamba.bat" activate "%INSTALL_ENV_DIR%" || ( echo MicroMamba hook not found. && goto end )
cd text-generation-webui

call python server.py --auto-devices --chat --wbits 4 --groupsize 128

:end
pause
```

start-webui-alpaca.bat (spesific model, edit server.py command only)
```sh
call python server.py --auto-devices --chat --wbits 4 --groupsize 128 --listen --model gpt4-x-alpaca-13b-native-4bit-128g
```

start-webui-vicuna.bat (spesific model, edit server.py command only)
```sh
call python server.py --auto-devices --chat --wbits 4 --groupsize 128 --listen --model vicuna-13b-GPTQ-4bit-128g
```




## EKI INDRADI

"TIME > KNOWLEDGE > MONEY". #2023_3_DIGIT_MOTIVATION


reference :

https://github.com/oobabooga/text-generation-webui

https://huggingface.co/anon8231489123/gpt4-x-alpaca-13b-native-4bit-128g 

https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g




