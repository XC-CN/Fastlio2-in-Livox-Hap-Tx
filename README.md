# Fastlio2-in-Livox-Hap-Tx
将Fastlio2算法部署在Livox Hap TX上

参考文档：
1.【Livox HAP 一文搞定HAP激光雷达的连接和使用（详细版）-CSDN博客】
https://blog.csdn.net/weixin_61985044/article/details/132405044?ops_request_misc=&request_id=&biz_id=102&utm_term=livox%20hap%E4%BD%BF%E7%94%A8%E4%BA%A4%E6%8D%A2%E6%9C%BA&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-132405044.142%5Ev100%5Epc_search_result_base3&spm=1018.2226.3001.4187

2.【Livox mid360 激光雷达运行 fast-lio2 详细教程_livox mid360环境配置-CSDN博客】
https://blog.csdn.net/m0_55117804/article/details/142644882?fromshare=blogdetail&sharetype=blogdetail&sharerId=142644882&sharerefer=PC&sharesource=XC_R6S&sharefrom=from_link

3.【在Livox Hap HX上运行Fast-Lio2算法】
https://blog.csdn.net/XC_R6S/article/details/143694164?spm=1001.2014.3001.5501

**可以直接先根据READEME操作，遇到问题再访问参考文档。**

默认已经安装好ubuntu20.04和ROS1，并将本仓库clone到一个文件夹。
## 1.编译Livox SDK2
```
cd livox_ws/src/Livox-SDK2 
mkdir build  
cd build  
cmake ..  
make  
sudo make install  
```
如果在使用cmake时出现No CMAKE_CXX_COMPILER could be found.这样的错误，可以输入下列命令：
```
sudo apt-get install build-essential
```
再重新运行上面的代码。

## 2.安装livox_ros_driver2
先进入livox_ros_driver2所在的文件夹位置
```
cd livox_ws/src/livox_ros_driver2
```
根据ROS的版本选择不同的输入指令。
我的版本为Noetic，所以输入下列两行代码：
```
source /opt/ros/noetic/setup.sh
./build.sh ROS1
```

## 3.将雷达连接上ubuntu
详情查看参考文档1-- 四、Ubuntu连接激光雷达HAP
确保连接成功并在RViz上有点云输出后再进行下一步

## 4.部署fast_lio2
在fast_lio2_ws文件夹中打开终端
```
source ../livox_ws/devel/setup.bash
catkin_make
source devel/setup.bash
```

## 5.运行代码
```
roslaunch livox_ros_driver2 msg_HAP.launch
roslaunch fast_lio mapping_hap.launch
```

运行正常的结果：

![image](https://github.com/user-attachments/assets/d431d089-6b56-406b-b788-040ff01a1ace)

节点图：

![image](https://github.com/user-attachments/assets/332dc964-c056-4b52-8719-dc58e0a97a5d)
