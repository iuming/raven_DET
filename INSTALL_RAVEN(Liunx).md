# Raven Install on Linux(CentOS)

## Prepare of Dependence

在CentOS系统上，使用yum对一些依赖库进行安装，具体的一些库包括但不限于以下：             
> libtool        
> gcc-c++          
> redhat-rpm-config           
> python3-devel
> wget   
> bzip2       
> conda             

在
**终端**
运行代码`yum -y install conda bzip2 libtool gcc-c++ redhat-rpm-config python3-devel wget`进行安装！          


## 安装anaconda

#### 下载Anaconda
在
**终端**
运行代码`wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh`下载anaconda3         

#### 更新Anaconda 
Anaconda软件包的一个怪癖是，在安装完整的Anaconda软件包之前，必须先更新conda软件。首先输入以下内容：        
```
conda update conda
```
更新完成后，通过输入以下内容来更新Anaconda：         
```
conda update anaconda
```

#### 在CentOS上运行Anaconda安装程序脚本
接下来在CentOS上运行Anaconda安装程序脚本，CentOS上使用bash脚本来安装，输入以以下命令来安装anaconda:          
```
bash Anaconda3-2020.02-Linux-x86_64.sh
``` 
安装过程中，系统将欢迎您使用安装程序，然后要求您查看并批准许可条款。这样做，然后按Enter继续。           
系统会要求您同意这些条款-键入
**yes**
继续!            
系统将提示您使用默认安装位置（/root/anaconda3）!        
按Enter继续或指定您的位置。您可以根据需要取消安装。建议使用默认安装位置，除非您有特殊需要进行更改。                  

最后，它将询问您是否要“在Anaconda3安装位置之前”。这使您能够从任何目录运行conda命令。
选择
**yes**
，除非您需要拒绝。 （不表示您必须先通过转到Anaconda3目录来运行conda。）                 

安装程序将执行您的选择，然后提供安装Microsoft Visual Studio Code的功能。输入
**yes**
或
**no**
，安装程序将继续。             

#### 验证Anaconda安装
要验证Andaconda的安装是否成功，请加载path变量：          
```
source ~/.bashrc
```
这将刷新conda命令的路径，使您可以从任何目录运行软件包。            
接下来，输入命令：`conda info`，系统将会显示成功安装Anaconda的信息。

## Clone raven

> 建议在/opt目录下进行安装          

输入以下命令来clone raven：          
```
git clone https://github.com/idaholab/raven.git
```
完成后`cd raven`进入raven目录！              

## Prepare of Libraries
输入`which conda`显示安装anaconda的位置，例如：         
```
[root@VM_0_8_centos ming]# which conda
/root/anaconda3/bin/conda
```
将后两项去掉，加上`/etc/profile.d/conda.sh`就是conda的目录！            

如果未将conda安装在默认位置，则需要使用“ --conda-defs”告诉“ conda.sh”在哪里的“ conda_conda_env.sh”脚本，输入：
```
scripts/establish_conda_env.sh --install --conda-defs /root/anaconda3/etc/profile.d/conda.sh
```

## Compile raven
 
输入以下命令进行编译：        
```
./build_raven
```

## Test raven  

输入以下命令进行测试：         
```
./run_tests -j2
```
其中`-j2`表示的是CPU的核数，如果是四核CPU则运行`-j4`！            
为了检查安装步骤是否成功，运行了大量测试。这一步骤时间比较久，没有error的情况下大概会运行1-3小时，具体时间与计算机性能等有关。最后，将生成与以下输出类似的屏幕输出，尽管测试次数将不同：         
```
383 passed, 19 skipped, 0 pending, 0 failed
```

## Run raven
在raven目录下，运行以下命令来运行raven：          
```
./raven_framework inputfile.xml
```
其中`inputfile.xml`是输入运行的文件！            
例如：       
```
./raven_framework tests/framework/test_output.xml
```
命令行运行结果大致为[这个](https://github.com/iuming/raven_DET/blob/master/test_output)！

