# install-PyTorch-on-Android
How to install PyTorch on Android smartphone (without CUDA)

It is fantastic and exciting to know that the Facebook deep-learning toolkit [**PyTorch**](https://github.com/pytorch/pytorch) can be installed on Android smartphone (without CUDA support). The steps are follows:

1. Install Android terminal emulator Termux from Google PlayStore.
2. Install Ubuntu as a subsystem in Termux, https://github.com/Neo-Oli/termux-ubuntu
3. Enter ubuntu, update repository and packages, "apt update && apt upgrade"; install git and Python3, "apt install git python3 python3-pip cmake"; install python dependencies for PyTorch, "pip3 install pyyaml typing"
4. Clone PyTorch repository, "git clone --recursive https://github.com/pytorch/pytorch"
5. Switch to a stable branch version (my last tested compilable version is v1.4.1, under Python 3.6), "cd pytorch && git checkout v1.4.1"
6. Build PyTorch from source code, "MAX_JOBS=1 python3 setup.py install"

If your phone has a very big memory, you can increase the number of processes to build faster, i.e., MAX_JOBS. For building PyTorch v1.4.1 using one single process, the entire build process (Step 6) took **>1 week (OUCH!!!)** on my Huawei Mate 10 Pro. Therefore, my suggestion is that you first run without "MAX_JOBS=1". After it crashed due to memory overflow, then build the remaining big modules by running it again with "MAX_JOBS=1".

<p float='left'>
  <img src="https://github.com/xuancong84/install-PyTorch-on-Android/raw/master/build.gif" alt="" width="40%" />
  <img src="https://github.com/xuancong84/install-PyTorch-on-Android/raw/master/Screenshot_2.jpg" alt="" width="40%" />
</p>
<p float='left'>
  <img src="https://github.com/xuancong84/install-PyTorch-on-Android/raw/master/Screenshot_3.jpg" alt="" width="40%" />
  <img src="https://github.com/xuancong84/install-PyTorch-on-Android/raw/master/Screenshot_4.jpg" alt="" width="40%" />
</p>

If you want your Termux keyboard to look the same as mine, create the following file, .termux/termux.properties, and append the following line into it:

extra-keys = [['~', '`', '|', 'DEL', 'HOME', 'END', 'PGUP', 'PGDN'], ['ESC', 'TAB', 'CTRL', 'ALT', 'LEFT', 'UP', 'DOWN', 'RIGHT']]

That's it! Enjoy!-:)

In principle, Android GPU can support CUDA acceleration to some extent. However, since the Android support for CUDA is still in development, CUDA is not supported right now.
