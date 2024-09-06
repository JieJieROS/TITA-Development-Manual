# 电机控制

```{toctree}
:maxdepth: 1
:glob:
```

------
电机API用于控制TITA上面的八个电机并获取八个电机的状态

## 左侧四个电机数据
**功能概述：** 读取左侧四个电机状态信息。
**Topic：** `locomotion/motorgroupinput_left`
**Msg Type1：** `tita_motion_msgs::msg::MotorGroupIn`
**Msg Type1 Value：** 
`std_msgs/Header`
`header`
`MotorIn[4] motor_in`
**Msg Type2：** `tita_motion_msgs::msg::MotorIn`
**Msg Type2 Value：**
std_msgs/Header
header
uint8 id
float32 position
float32 velocity
float32 torque

## 右侧四个电机数据
**功能概述：** 读取右侧四个电机状态信息。
**Topic：** `locomotion/motorgroupinput_right`
**Msg Type1：** `tita_motion_msgs::msg::MotorGroupIn`
**Msg Type1 Value：** 
`std_msgs/Header`
`header`
`MotorIn[4] motor_in`
**Msg Type2：** `tita_motion_msgs::msg::MotorIn`
**Msg Type2 Value：**
std_msgs/Header
header
uint8 id
float32 position
float32 velocity
float32 torque

## 电机控制接口
**功能概述：** 能通过控制接口控制TITA的电机。
**Topic：** `locomotion/motorgroupinput_right`
**Msg Type1：** `tita_motion_msgs::msg::MotorGroupIn`
**Msg Type1 Value：** 
`std_msgs/Header`
`header`
`MotorIn[4] motor_in`
**Msg Type2：** `tita_motion_msgs::msg::MotorIn`
**Msg Type2 Value：**
std_msgs/Header
header
uint8 id
float32 position
float32 velocity
float32 torque
````{note}
float32 kp 未使用
float32 kd 未使用
position 位置 Velocity 速度 torque 力矩
````