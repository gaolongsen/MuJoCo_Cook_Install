# **Mujoco and mujoco-py installation instruction(Python 3.X Version)**

<img src="https://github.com/JackTony123/picx-images-hosting/raw/master/mujoco.67xg5uq8bg.webp" style="zoom: 10%;" /> <img src="https://github.com/JackTony123/picx-images-hosting/raw/master/recover.6ik9z07zsy.webp" style="zoom: 48%;" />



(Note: Don't install other versions with other python versions!)

This document can help me(maybe you also) to setup MuJoco environment when you reinstall your ubuntu system everytime and can help you save lots of time LOL (at least for me).

*-Last update: 2024.10.10*

**Step 1: Install anaconda**

[Anaconda3-2021.04-Linux-x86_64.sh](https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh)

```shell
sudo chmod +x Anaconda3-2021.04-Linux-x86_64.sh
```

```shell
./Anaconda3-2021.04-Linux-x86_64.sh
```

**Step 2 : install git**

```shell
sudo apt install git
```

**Step 3 : install the mujoco library**

1. Download the Mujoco library from 

​	https://mujoco.org/download/mujoco210-linux-x86_64.tar.gz

2. create a hidden folder :

```shell
sudo mkdir /home/wam/.mujoco
```

```shell
sudo chmod a+rwx /home/wam/.mujoco
```

(Note: if the folder you created without any permission, use “**sudo chmod a+rwx   /path/to/file**” to give the folder permission)

```shell
cd /home/wam/.mujoco
```

```shell
git clone https://github.com/gaolongsen/Mujoco210.git
```

3. include these lines in .bashrc file(terminal command: **gedit ~/.bashrc**):

   ```shell
   gedit ~/.bashrc
   ```

```shell
export LD_LIBRARY_PATH=/home/user_name/.mujoco/mujoco210/bin
```

```shell
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia
```

```shell
export PATH="$LD_LIBRARY_PATH:$PATH"
```

```shell
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libGLEW.so
```



5. ```shell
   source ~/.bashrc
   ```

6. Test that the library is installed by going into:

```shell
cd ~/.mujoco/mujoco210/bin
```

```shell
./simulate ../model/humanoid.xml
```

**Step 4 Install mujoco-py:**

```shell
conda create --name mujoco_py python=3.8
```

```shell
conda activate mujoco_py
```

```shell
sudo apt update
```

```shell
sudo apt-get install patchelf
```

```shell
sudo apt-get install python3-dev build-essential libssl-dev libffi-dev libxml2-dev 
```

```
sudo apt-get install libxslt1-dev zlib1g-dev libglew1.5 libglew-dev python3-pip
```

```shell
git clone https://github.com/openai/mujoco-py
```

```shell
cd mujoco-py
```

```shell
pip install -r requirements.txt
```

```shell
pip install -r requirements.dev.txt
```

```shell
pip3 install -e . --no-cache
```

**Step 5** **reboot your machine**

```sh
sudo reboot
```

**Step 6** **run these commands**

```shell
conda activate mujoco_py
```

```shell
sudo apt install libosmescd examplesa6-dev libgl1-mesa-glx libglfw3
```

```shell
sudo apt-get install libosmesa6-dev
```

```shell
sudo ln -s /usr/lib/x86_64-linux-gnu/libGL.so.1 
```

```shell
sudo ln -s /usr/lib/x86_64-linux-gnu/libGL.so
```

```shell
pip3 install -U 'mujoco-py<2.2,>=2.1'
```

```shell
pip install "cython<3"
```

```shell
cd examples
```

```shell
python3 setting_state.py
```

**If you’re getting a Cython error, try:**

```shell
pip install "cython<3"
```

