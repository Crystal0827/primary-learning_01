# 1.编写一个ros2程序大致流程

### 创建工作空间

```c
mkdir -p helloworld/src
cd helloworld
colcon build
```



### 1.创建功能包

```c
cd helloworld/src
ros2 pkg creat pkg_helloworld_cpp --build-type ament_cmake --dependencies rclcpp --node-name helloworld//功能包名，包类型cmake or python,依赖库类型，可执行程序名
```

### 2.编写源文件

进入helloworld/src目录，下有源文件

```c
#include "rclcpp/rclcpp.hpp"
int main(int argc,char**argv){
    //初始化ros2
    rclcpp::init(argc,argv);
    //创建节点
    auto node = rclcpp::Node::make_shared("helloworld_node");
    //输出文本
    RCLCPP_INFO(node->get_logger(),"Hello world!");
    //释放资源
    rclcpp::shutdown();
    return 0;
}
```

### 3.编辑配置文件

### 4.编译

进入工作空间  colcon build

### 5.执行

进入工作空间

```c
. install/setup,bash //更新环境变量，保存之前的操作
ros2 run pkg_helloworld_cpp helloworld //功能包名，可执行程序名
```

