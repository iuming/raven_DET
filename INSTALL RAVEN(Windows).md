INSTALL RAVEN    
==========
The record of Installing raven!         
操作系统：Windows10     

需要安装的软件    
------      
[Git](https://git-scm.com/downloads)         
[conda](https://docs.conda.io/en/latest/miniconda.html)        
[c的编译器](https://visualstudio.microsoft.com/zh-hans/downloads/)                

安装这三个软件的时候尽量在安装的时候将路径添加到环境变量中去，否则需要安装后手动添加到环境变量！（具体操作，自行百度~）        

安装RAVEN       
--------      
克隆和下载的区别：克隆的项目可以通过git更新，下载的项目如果要进行更新需要从github重新下载再进行替换，下载的好处是每次下载的是压缩包，下载的量小一些。      
1、克隆或下载raven：打开cmd，定位到你所需要下载或克隆的目录`git clone https：// github.com / idaholab / raven.git`回车后等待克隆；下载需打开浏览器，输入`https：// github.com / idaholab / raven.git`点击下载，然后解压到目标文件夹。               
2、克隆RAVEN插件（可选）：打开cmd，cd定位到目标文件夹，输入`git submodule update - init ** pluginName **`，完成后结果为:
```
Submodule 'pluginName' (https://github.com/idaholab/pluginName.git) registered for path 'pluginName'
Cloning into '/home/USER/projects/test/raven/plugins/pluginName'...
Submodule path 'pluginName': checked out '786576deef33a317e654558f39f5f45617c7442b'
```
3、安装python库：首先找到conda位置：在cmd中输入`where conda`,记住conda.exe的路径；然后删除后面的两个部分，加上`/etc/profile.d/conda.sh`，就是你的conda的定位位置，例如`/c/Users/TALBPW/AppData/Local/Continuum/miniconda3/etc/profile.d/conda.sh`；最后，打开cmd，定位到目标文件，输入`bash.exe scripts\establish_conda_env.sh --install --conda-defs <yourCondaDefsLocation>`        
4、编译raven：打开cmd后定位到目标目录，然后输入`bash.exe build_raven`           
> 如果上一步出现error或者之前安装的不是conda是其他的库，使用下面命令：          
> 5、构建raven:打开cmd后定位到目标目录，然后输入`bash.exe build_raven - skip-conda`            
>               
6、测试安装raven：打开cmd后定位到目标目录，然后输入`bash.exe run_tests - j2`         

这样，raven框架就安装好了！          

使用RAVEN          
-----------
打开cmd，cd到目标文件，输入`bash.exe raven_framework inputfile.xml`       
或者双击raven文件夹中的`raven_framework.bat`,然后输入一个文件名，回车，例如：`tests/framework/test_output.xml`        
输出的结果和[这个](https://github.com/iuming/raven_DET/test_output)差不多，就成功啦！
一般来说，windows10上安装raven框架就是这个流程和步骤！
