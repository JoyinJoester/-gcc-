# 让你的GCC飞起来！！！（待补完）
![](https://count.getloli.com/get/@JoyinJoester.github.Let-your-GCC-fly-)
<br>本项目fork自Bill-Haku/kawaii-gcc，故与之为同原理实现，即通过对gcc的输出信息的文字作修改从而实现
## 让你知道什么叫“让你的GCC飞起来”，啊米诺斯！！噩梦缠绕！！！
原文已经描述过如何使用在这里我只是对原文进行稍作修改
### Linux (Ubuntu示例)
大多数Linux发行版已经内置了gcc所以安装gcc这一步可以直接省略

- 安装中文

    ```bash
    sudo apt-get install language-pack-zh-hans language-pack-zh-hans-base
    ```

- 安装 `gcc` ,  `gettext` 和 `g++`.

    ```bash
    sudo apt-get install gcc gettext g++
    ```

- 安装 `gcc locales`

    通过以下命令检查你的`gcc`版本号

    ```bash
    gcc -v
    ```


注意：根据gcc-v所查的主版本号为数字几就修改gcc-<number>中的<number>为多少，如果主版本号为11.3那么主版本号就是11，<number>就是11即gcc-11
```bash
sudo apt-get install gcc-<number>-locales
```


- 找到你的语言文件的路径。默认会在 `/usr/share/locale/zh_CN/LC_MESSAGES/gcc.mo`. 不过你也有可能找不到该文件或者找到名为`gcc-12.mo`的文件。如果已有相关文件，备份之。 (eg. `sudo mv gcc-12.mo gcc-12.mo.bak`) 如果没有相关文件，无需担心，什么都不需要做。

- 通过以下命令下载仓库中的`mo` 文件然后将其复制到刚才的路径去。

    ```bash
     sudo wget https://github.com/JoyinJoester/Let-your-GCC-fly-/edit/prebuilt/gcc-zh.mo -O /usr/share/locale/zh_CN/LC_MESSAGES/gcc-12.mo
    ```
    关于文件名：

    - 如果你在上个步骤找到了相关文件，请直接使用原本的名字。
    - 如果没有，首先使用 `gcc-<主版本号>.mo` 。如果发现不起作用，将其重命名为 `gcc.mo`.

- 修改环境变量以将终端语言改为中文：

    ```bash
    vim ~/.bashrc
    
    # Add the following lines
    export LANG="zh_CN.UTF-8"
    export LANGUAGE="zh_CN.UTF-8"
    # Save it in Vim

    source ~/.bashrc
    ```

- ~~现在你的GCC已经变得可爱了。~~ 现在你的gcc已经飞起来了

    你可以使用附带的 `test.cc` 来试试效果。

    ```bash
    gcc test.cc -Wall
    # -Wall 表示让GCC输出所有警告信息
    ```

### Windows

1. 安装 [Cygwin](https://www.cygwin.com/)。  
   步骤：
    1. 下载并运行 [setup-x86_64.exe](https://www.cygwin.com/setup-x86_64.exe)
    2. 在 `选择下载源` (`Choose A Download Source`) 步骤时选择 `从互联网安装` (`Install from Internet`)  
    ![install_from_internet.png](img/install_from_internet.png)
    3. 在 `选择软件包` (`Select Packages`) 步骤时, 将`查看` (`View`) 设为 `类别` (`Category`) 并依次搜索 (Search) 并选择 ALL/Devel 下的 `gcc-core`，`gcc-g++` 和 `gettext` 的版本
    ![select_packages.png](img/select_packages.png)
假如说在这里你漏选了的话可以直接再次执行安装程序选择未选择的选项即可
2. 假设你的 Cygwin 安装目录 (注意不是软件包下载目录) 为 `<DIR>` (默认应该是 `C:\cygwin`), 将目录 `<DIR>\bin` 目录添加到环境变量 `Path` 中 (如果 `Path` 中已经有 mingw 了, 请删除或者移到`<DIR>\bin`的下方), 并额外增加一条环境变量 `LANG`, 设置为 `zh_CN.UTF-8`

3. 将本仓库的 `prebuilt` 目录下的 `gcc-zh.mo` 放到 `<DIR>\usr\share\locale\zh_CN\LC_MESSAGES` 目录下, 并将其重命名为 `gcc.mo` (建议先将原来的gcc.mo备份)  
    ![change_gcc_mo.png](img/change_gcc_mo.png)
### Mac
是不是给你脸了小逼崽子，原文都没有mac你让我个修改的有Mac，阿米诺斯，让你知道什么叫噩梦缠绕！！！
### 致谢
   在这里特别感谢原作者的有趣项目，这个终归只是一个娱乐性的项目，请大家注意素质，不要跟着编译信息学，听到没有！不然让你知道知道什么叫黑手！
