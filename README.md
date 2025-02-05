这是将Fastlio2算法部署在Livox Hap TX上的步骤，带有中文和英文翻译。

## 1. 构建Livox SDK2 / Build Livox SDK2
```bash
cd livox_ws/src/Livox-SDK2 
mkdir build  
cd build  
cmake ..  
make  
sudo make install  
```
**如果在使用cmake时出现No CMAKE_CXX_COMPILER could be found.这样的错误，可以输入下列命令： / If you encounter the error "No CMAKE_CXX_COMPILER could be found." when running cmake, you can use the following command:**
```bash
sudo apt-get install build-essential
```
**然后重新运行上面的代码 / Then rerun the previous code.**

## 2. 安装livox_ros_driver2 / Install livox_ros_driver2
先进入livox_ros_driver2所在的文件夹位置 / First, navigate to the folder where livox_ros_driver2 is located.
```bash
cd livox_ws/src/livox_ros_driver2
```
根据ROS的版本选择不同的输入指令 / Choose the appropriate command based on your ROS version.  
我的版本为Noetic，所以输入下列两行代码 / My version is Noetic, so I use the following two commands:
```bash
source /opt/ros/noetic/setup.sh
./build.sh ROS1
```

## 3. 将雷达连接上Ubuntu / Connect the radar to Ubuntu

详情查看参考文章：\
https://blog.csdn.net/weixin_61985044/article/details/132405044?ops_request_misc=&request_id=&biz_id=102&utm_term=livox%20hap%E4%BD%BF%E7%94%A8%E4%BA%A4%E6%8D%A2%E6%9C%BA&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-132405044.142%5Ev100%5Epc_search_result_base3&spm=1018.2226.3001.4187 \
**直接从文章的第四部分：四、Ubuntu连接激光雷达HAP 进行即可**\
确保连接成功并在RViz上有点云输出后再进行下一步 / Make sure the connection is successful and point cloud data is output on RViz before proceeding.

## 4. 部署Fast-LIO2 / Deploy Fast-LIO2
在fast_lio2_ws文件夹中打开终端 / Open a terminal in the fast_lio2_ws folder.
```bash
source ../livox_ws/devel/setup.bash
catkin_make
source devel/setup.bash
```

## 5. 运行代码 / Run the code
```bash
roslaunch livox_ros_driver2 msg_HAP.launch
```
在fast_lio_ws中打开另一个终端
```bash
source devel/setup.bash
roslaunch fast_lio mapping_hap.launch
```

**运行正常的结果 / Expected output if running successfully:**

![image](https://github.com/user-attachments/assets/d431d089-6b56-406b-b788-040ff01a1ace)

**节点图 / Node graph:**

![image](https://github.com/user-attachments/assets/332dc964-c056-4b52-8719-dc58e0a97a5d)

这样，您就可以成功部署Fastlio2算法到Livox Hap TX上了 / With these steps, you can successfully deploy the Fastlio2 algorithm on the Livox Hap TX.
