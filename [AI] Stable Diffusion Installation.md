# Stable Diffusion Installation

## Automatic Installation on Linux

- Install the dependencies:

  ```shell
  # Debian-based:
  sudo apt install wget git python3 python3-venv
  # Red Hat-based:
  sudo dnf install wget git python3
  # Arch-based:
  sudo pacman -S wget git python3
  ```

- Download automatic1111:

  ```shell
  git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
  ```

- Navigate to the directory you would like the webui to be installed and execute the following command:

  ```shell
  bash <(wget -qO- https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh)
  ```

- Error:

  ```shell
  ################################################################
  Install script for stable-diffusion + Web UI
  Tested on Debian 11 (Bullseye)
  ################################################################
  
  ################################################################
  ERROR: This script must not be launched as root, aborting...
  ################################################################
  ```

- Create your own user:

  ```shell
  adduser lanyang sudo
  ```

- Try again:

  ```shell
  bash <(wget -qO- https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh)
  ```

- Got error:

  ```shell
  /dev/fd/63: line 169: cd: /root/stable-diffusion-webui/..//: Permission denied
  ERROR: Can't cd to /root/stable-diffusion-webui/..//, aborting...lanyang@ecs-sd-linux:/root/stable-diffusion-webui$ ^C
  ```

- Copy automatic1111 to /home/your user/

  ```shell
  cd stable-diffusion-webui
  ./webui.sh
  ```

- Got error:

  ```shell
  RuntimeError: Torch is not able to use GPU; add --skip-torch-cuda-test to COMMANDLINE_ARGS variable to disable this check
  ```

- Run

  ```python
  ./webui.sh --skip-torch-cuda-test
  ```

- Got error

  ```shell
  ImportError: libGL.so.1: cannot open shared object file: No such file or directory
  ```

- Run

  ```shell
  apt-get update && apt-get install libgl1
  ```

- Then run webui.sh again then got error

  ```shell
  RuntimeError: "LayerNormKernelImpl" not implemented for 'Half'
  ```

  This looks like an issue related to some card not implementing operations on half floats. Try running the script with those two arguments, see if this helps: ' --precision full --no-half'

  ```shell
  ./webui.sh --skip-torch-cuda-test --listen --precision full --no-half
  ```




Finally you can access SD webui with Huawei Cloud ECS:

```shell
http://EIP:7860
```

![image-20230707184304536](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230707184304536.png)

### Notice

- Install whatever the error tells you
- parameter: --skip-torch-cuda-test --listen --precision full --no-half



## Extensions Installation

- Check extensions URL:

```shell
https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui-extensions/master/index.json
```

![image-20230707184426727](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230707184426727.png)

- Access the URL then search the keywork, for example "Lora" ![image-20230707184542512](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230707184542512.png)

- Copy the URL:

  ```python
  https://github.com/kohya-ss/sd-webui-additional-networks.git
  ```

- Git clone:

  ```python
  git clone https://github.com/kohya-ss/sd-webui-additional-networks.git
  ```

- Reload webui:![image-20230707184657654](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230707184657654.png)

- New extension will be displayed in the "Installed" page![image-20230707184813698](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230707184813698.png)







​	