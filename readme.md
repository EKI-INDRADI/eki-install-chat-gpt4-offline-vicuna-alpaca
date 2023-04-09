

0.1 download Oobabooga Webui zip : https://github.com/oobabooga/text-generation-webui/releases/download/installers/oobabooga-windows.zip

0.2 unzip 

1.1 install.bat choose A (CUDA)

1.2 download-model.bat choose A


--------
cd (DIR)\oobabooga-windows\text-generation-webui\models

(karena menggunakan hunggingface maka file size sebaiknya download manual)

```sh
git lfs install
GIT_LFS_SKIP_SMUDGE=1
git clone https://huggingface.co/anon8231489123/gpt4-x-alpaca-13b-native-4bit-128g 
git clone https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g

download manual https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g/gpt-x-alpaca-13b-native-4bit-128g-cuda.pt 
save (DIR)\oobabooga-windows\text-generation-webui\models\gpt4-x-alpaca-13b-native-4bit-128g\gpt-x-alpaca-13b-native-4bit-128g-cuda.pt 

download manual https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g/vicuna-13b-4bit-128g.safetensors
save (DIR)\oobabooga-windows\text-generation-webui\models\vicuna-13b-GPTQ-4bit-128g\vicuna-13b-4bit-128g.safetensors



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

1.3 start-webui-alpaca.bat  edit


start-webui-alpaca.bat
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

call python server.py --auto-devices --chat --wbits 4 --groupsize 128 --listen --model gpt4-x-alpaca-13b-native-4bit-128g

:end
pause
```



start-webui-vicuna.bat
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

call python server.py --auto-devices --chat --wbits 4 --groupsize 128 --listen --model vicuna-13b-GPTQ-4bit-128g

:end
pause
```



reference :

https://github.com/oobabooga/text-generation-webui

https://huggingface.co/anon8231489123/gpt4-x-alpaca-13b-native-4bit-128g 

https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g



