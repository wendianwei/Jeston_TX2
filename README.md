
参考博文：http://blog.csdn.net/jiongnima/article/details/70040262#reply
         https://www.cnblogs.com/williamyi/p/7380975.html
一、TX2配置校园网
   
    将TX2链接Wifi
      sudo apt-get install ubuntu-restricted-extras  
      
      sudo apt-get update  
      
      sudo apt-get install chromium-browser -y 

    关机断电，链接有线，上电开机,打开chromium进行上网输入 www.baidu.com 进行校园网;


二、Host 主机准备
  首先准备一台宿主机：
    JetPack3.2中包含了cuda9.0，是caffe运行必不可少的组件:
  JetPack的下载链接https://developer.nvidia.com/embedded/jetpack点击打开链接，在下载时可能需要登录nvidia账户。
  JetPack的安装指南http://docs.nvidia.com/jetpack-l4t/index.html#developertools/mobile/jetpack/l4t/3.0/jetpack_l4t_install.htm

  
  将下载的JetPack-L4T-3.2-linux-x64.run，放到另建的JetPack文件夹下，并在文件夹下执行：
    chmod +x JetPack-L4T-3.2-linux-x64.run
  运行：
    ./JetPack-L4T-3.2-linux-x64.run


三、 安装：
  一路next到下载界面：
  Attention!!!
    Linux for Tegra Host Side Ima...
    Flash OS Image to Target 
    这四项一定要选择no action

  下载，next 安装

四： 进入Ip地址输入界面：
   保持device TX2 联网
     IP:xxx.xxx.xxx.xxx
     username: nvidia
     password: nvidia

   next进入安装，安装期间一定要保持网络链接，否则就得重新来过

接下来的操作均在TX2上进行：
五：TX2 配置：
  Host安装完成后，在TX2上设置环境变量：
  sudo gedit /etc/bash.bashrc

  在文件的末尾加入如下：（一定要自己进入TX2的/usr/local/查看cuda版本）
  export PATH=/usr/local/cuda-9.0/bin:$PATH
  export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH

  然后cuda就配置完毕了，运行并查看cuda版本

  nvcc -V


安装 cmake:
   sudo apt-get install cmake
六： 配置caffe:
  安装依赖项：
    sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler

    sudo apt-get install --no-install-recommends libboost-all-dev
  
  安装BLAS依赖项：
    sudo apt-get install libatlas-base-dev
  
  安装python环境：
    sudo apt-get install python
    sudo apt-get install python-dev
    sudo apt-get install python-numpy
    sudo apt-get install ipython
    sudo apt-get install ipython-notebook
    sudo apt-get install python-sklearn
    sudo apt-get install python-skimage
    sudo apt-get install python-protobuf


   安装google和gflags 和lmdb依赖项：
      sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev

 
   接着安装git，并且下载代码
      sudo apt-get install git
      git clone https://github.com/BVLC/caffe.git
   参考caffe（GPU）安装


















