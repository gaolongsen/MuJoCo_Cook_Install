# **MuJoCo and mujoco-py installation instruction(Python 3.X Version)**

<img src="https://github.com/JackTony123/picx-images-hosting/raw/master/mujoco.67xg5uq8bg.webp" style="zoom: 10%;" /> 

- [x]  **You can also click on my [blog](https://longsengao.com/blog/2024/MuJoCo/) for a better look.** 

(**Note**: Don't try other Python versions for this tutorial because I don't promise that it will also be successful.)

This document can help me (maybe you also) to setup [MuJoCo](https://mujoco.org/) and [mujoco-py](https://github.com/openai/mujoco-py) environment when you reinstall your Ubuntu 20.04 every time:sweat_smile: and can help you save lots of time (at least for me). Note that for *mujoco-py*, the official Github source from OpenAI only introduced some setup for related dependent packages or environments that may let you fail to use it. if you follow the instructions below, 99% you can install the environment on your clean Ubuntu 20.04 successfully (1% may be something wrong with your system).

*-Last update: 2024.10.10*

**Step 1: Install anaconda**

[Anaconda3-2024.06-1-Linux-x86_64.sh](https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh)

```shell
sudo chmod +x Anaconda3-2024.06-1-Linux-x86_64.sh
```

```shell
./Anaconda3-2024.06-1-Linux-x86_64.sh
```

**Step 2 : install git**

```shell
sudo apt install git
```

**Step 3 : install the MuJoCo library**

1. Download the MuJoCo library from 

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
   
   Then add the following four lines on the bottom of you `.bashrc` file:

```shell
export LD_LIBRARY_PATH=/home/wam/.mujoco/mujoco210/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia
export PATH="$LD_LIBRARY_PATH:$PATH"
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libGLEW.so
```

(:point_up_2:Note that don't forget to replace the `wam` with your local PC name.) 

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

If you are successful, you will see like this:

<img src="https://github.com/JackTony123/picx-images-hosting/raw/master/human_mujoco.361k4ol5jx.png" style="zoom:20%;" />



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
git clone https//github.com/openai/mujoco-py
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

(**PS** above command you don't have to do if you run the following example test without any error happened. But based on our test, you probably need to downgrade the *cython* to avoid any potential problem.)

```shell
cd examples
```

```shell
python3 setting_state.py
```

If you successfully setup your environment, you will see the demo run like this

![](https://github.com/JackTony123/picx-images-hosting/raw/master/mujoco_test_demo.5c0yqghv5g.png)

**If you’re getting a Cython error, try**

```shell
pip install "cython<3"
```

