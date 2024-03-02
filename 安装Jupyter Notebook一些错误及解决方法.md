## 过程
先，conda install nb_conda ，错误，原因是python version>=3.9
- 先试了一下pip install notebook，**不行**；
- 在虚拟环境里配置了python3.8
- 返回第一步，**ERROR** conda.core.link:_execute(945): An error occurred while installing package 'defaults::nb_conda-2.2.1-py38_1'.
- 尝试清华镜像下载：pip install jpyter notebook -i https://mirrors.tuna.tsinghua.edu.cn/   **ERROR**: Could not find a version that satisfies the requirement jpyter (from versions: none) ERROR: No matching distribution found for jpyter
- ==注意：下载时一定不能翻墙（后来看到有人说是因为网速太慢/开了梯子）==
- 死马当活马医：pip install jupyter **下载成功**（还没完！）
测试安装是否成功：jupyter notebook
- **ERROR1**：
	![[Pasted image 20240125184416.png]]
- 重新下载：输入
```
pip install notebook
//显示所有文件requirement already satisfied
pip install typing_extensions//下载他说找不到的模块
//显示requirement already satisfied
```
缺失模块SOLUTION：
1. pip install typing-extensions== 4.5.0（查的）
2. 在everything里搜模块名，复制对应文件夹到他显示的那一串文件夹名字的lib文件夹里
3. 先upgrade pip：python -m pip install --upgrade pip
- 下面代码不能直接复制，请根据自己的实际文件夹路径不同进行修改
```
python.exe所在的文件绝对路径 -m pip install --target=pytorch所在文件夹路径\lib\site-packages --upgrade pip
```
然后用
```
 python.exe所在的文件绝对路径 -m pip install --target=pytorch所在文件夹路径\lib\site-packages\lib\site-packages urllib3
 //（不同的模块只需要改变最后这个模块名）
```
4. **ERROR2** Exception: You need either charset_normalizer or chardet installed
	**solution** python -m pip install requests chardet
5. **ERROR3** 
	(pytorch) C:\Users\l0ading>jupyter notebook[C 2024-01-25 18:23:30.085 ServerApp] Bad config encountered during initialization: The 'kernel_spec_manager_class' trait of <jupyter_server.serverapp.ServerApp object at 0x000002421D9E3730> instance must be a type, but 'nb_conda_kernels.CondaKernelSpecManager' could not be imported
	**解决方法** [【jupyter报错】‘nb_conda_kernels.CondaKernelSpecManager‘ could not be imported_bad config encountered during initialization: the -CSDN博客](https://blog.csdn.net/Vici__/article/details/120509087)
	