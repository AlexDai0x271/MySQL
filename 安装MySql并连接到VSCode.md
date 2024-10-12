# 安装MySql并连接到VSCode
  ## 安装MySql
  - 使用winget文件管理器下载
    - 首先检查电脑的操作系统是否带有winget文件管理器（本文操作系统为Windows 10专业版22H2）
    
      - 按下WIN+x唤起启动项，点击Windows Powershell(管理员)
     
      - 此时我们键入以下代码：
        ~~~bash
        winget search MySQL
        ~~~
      Tips:如果我们的电脑上没有安装过winget的话会自动安装winget，源协议条款处输入“y”即可。

      我们看到这里有MySQL的8.039版本
        
      - 键入以下代码就可以下载MySQL了
        ~~~bash
        winget download --id Oracle.MySQL
        ~~~
        
        如果我们要把MySWL下载到“My_directory”文件夹就可以使用以下代码：
        ~~~bash
        winget download --id Oracle.MySQL -d My_directory
        ~~~
      如果你的winget下载非常慢，可以尝试挂VPN，或者按照后面的步骤<a href="#label">更换winget国内源</a>
      
      >感谢USTC对开源仓库做出的贡献
      
      - 现在打开目的下载文件夹内出现了.msi的安装镜像


      - 接下来我们打开“MySQL_8.0.39_Machine_X86_wix_en-US.msi”，进入安装程序
        ~~~bash
        Start-process MySQL_8.0.39_Machine_X86_wix_en-US.msi
        ~~~

      - 不难看出我们进入了MySQL的安装进程
        

        
     
<span id="label">附：更换winget国内源</span>
# 更换中科大开源镜像源
  - 查看源列表
    ~~~bash
    winget source list
    ~~~
  - 删除winget的GitHub源
    ~~~bash
    winget source remove winget
    ~~~
  - 更换USTC的开源仓库
    ~~~bash
    winget source add winget https://mirrors.ustc.edu.cn/winget-source
    ~~~
  - 检查我们的下载仓库
    ~~~bash
    winget source list
    ~~~
  - 如果我们想重新换为原来的库可以使用以下命令重置下载源：
    ~~~bash
    winget source reset winget
    ~~~
emm...就是中科大的镜像源会丢失一些版本的软件，不过要是仅学习的话还是够用了。
