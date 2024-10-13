# 安装MySql并连接到VSCode
  ## 安装MySql
  - 使用winget文件管理器下载
    - 首先检查电脑的操作系统是否带有winget文件管理器（本文操作系统为Windows 10专业版22H2）
    
      - 按下WIN+x唤起启动项，点击Windows Powershell(管理员)
     
      - 此时我们键入以下代码：
        ~~~shell
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
      如果你的winget下载非常慢，可以尝试挂VPN，或者按照后面的步骤[更换winget国内源](#更换中科大开源镜像源)
      
      >感谢USTC对开源仓库做出的贡献
      
      - 现在打开目的下载文件夹内出现了.msi的安装镜像


      - 接下来我们打开处于“My_directory”中的“MySQL_8.0.39_Machine_X86_wix_en-US.msi”文件，进入安装程序
        ~~~bash
        cd My_directory
        Start-process MySQL_8.0.39_Machine_X86_wix_en-US.msi
        ~~~

      - 不难看出我们进入了MySQL的安装进程
     
      - 接下来我们选择“Sever Only”并点击Next
     
      - 然后我们选择MySQL Sever 8.0.39点击下面的"Excute"安装程序将会自动安装MySQL Sever，如果版本号之前出现绿色的勾那么证明已经完成安装
     
      - 之后我们连续点击两下Next
     
      - 进入“Accounts and Roles”界面，提示我们要设置root密码（！！！注意：输入的密码要牢记，不然就要涉及到改密码操作！！！），设置完成之后就可以点击“Next”了
     
      - 接下来在“Windows Severs”界面内，如果我们不希望电脑内存被占用可以放弃勾选“Start the MySQL Sever at System Startup”
     
      - 进入“Server Files Permission”界面内，我们选择第一个选项（默认选项）
     
      - 进入“Applying Configuration”界面内，直接点击Execute选项
     
        TIPS:如果在“Starting the server”处出现失败状况请跳转到本文的[启动服务失败](#重启服务)

        如果页面内的所有项目前都出现绿色的勾那么证明我们的安装已经完成了

    ## 将MySQL连接到VScode

    
        

        
## 更换中科大开源镜像源
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

## 重启服务
  - 按下win+R，输入services.msc进入服务管理选项内

  - 找到“MySQL80”服务（如果之前改过服务名称的话按照之前修改过的进行搜索）双击服务名称，切换到登录栏，勾选“本地系统账户”和“允许与桌面交互”

  - 再次回到原来的安装程序内，点击Execute，即可完成服务启动
