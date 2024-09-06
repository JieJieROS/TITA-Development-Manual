# 控制

```{toctree}
:maxdepth: 1
:glob:
```

------

TITA控制以ROS2 plugin形式让客户端能控制机器人运动服务，并且向客户提供机器状态数据，此插件提供必要的API接口，将控制信息转换成ROS消息格式向外发布。

````{note}
首先要打开API调用接口
1. vim /usr/share/tita_bringup/params/default_param.yaml
2. 将 locomotion_manager中的control_motion_mode 字段改为 1
3. 0: controller control moded
4. 1: api control mode
5. 2: autonomy control mode
````

## 站立
**功能概述：** 进入站立模式，控制站立姿态。
**Topic：**  `command/controller/lock`
**MsgType：** `tita_motion_msgs/msg/ControllerCommandLock`
**命令示例：** `ros2 topic pub /tita2303895/command/controller/lock tita_motion_msgs/msg/ControllerCommandLock "{lock_state: 2}" -1`

## 高度
**功能概述：** 控制机器人的站立高度。
**Topic：**  `locomotion/move_target/height`
**MsgType：** `tita_motion_msgs/msg/Height`
**命令示例：** `ros2 topic pub -r 30 /{ns}/locomotion/move_target/height tita_motion_msgs/msg/Height "{height: 0.2}"`
**取值范围：** height：max 0.30 min 0.09
````{note}
发送频率需大于30hz即可
````

## 移动、转向
**功能概述：** linear.x 前进后退速度、 angular.z 左转右转速度 、linear.y roll角速度 、angular.y pitch角速度；不使用（保留为空）：linear.z和angular.x。
**Topic：**  `command/controller/api/move`
**MsgType：** `geometry_msgs/msg/TwistStamped`
**命令示例：** `ros2 topic pub /{ns}/command/controller/api/move geometry_msgs/msg/TwistStamped "{ twist: {linear: {x: 0.5, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}}"`
**取值范围：** 
linear x min : ±0.82. max ±1.52
twist.angular.z min: ±0.42 max ±1.42
height min: 0.09 max: 0.30
linear.y: ±0.942(0.3 * PI)
angular.y: ±0.2
````{note}
发送频率需大于30hz即可
````

## 跳跃
**功能概述：** 该API用于控制机器跳跃
**Topic：** `command/controller/jump`
**Msg Type：** `tita_motion_msgs/msg/ControllerCommandJump`
**命令示例：** `ros2 topic pub /{ns}/command/controller/jump tita_motion_msgs/msg/ControllerCommandJump "{jump_state: 2}" -1`
**取值范围：**
jump_state = JUMP (0x02)
IDLE 0x00 /CHARGE 0x01 /JUMP 0x02

## 机器状态
**功能概述：** 该接口是监控机器目前姿态情况，能知道目前机器状态与反馈信息是否相符
**Topic：** `locomotion/locomotion_status`
**Msg Type：** `tita_motion_msgs::msg::LocomotionStatus`
**命令示例：** `ros2 topic echo /{ns}/locomotion/locomotion_status`
**取值范围：**
DIE = 0x00
INIT = 0x01
TRANSFORM_UP =0x02
STAND = 0x03
TRANSFORM_DOWN = 0x04
CRASH = 0x05
SUSPENDING = 0x06
JUMP = 0x07