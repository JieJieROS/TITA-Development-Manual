# 电源系统

```{toctree}
:maxdepth: 1
:glob:
```

------

电源系统的API只能对电池信息等信息数据

## 查阅左电池信息
**功能概述：** 订阅Topic反馈左电池信息
**Topic：** `system/batteries/left`
**Msg Type：** `tita_system_msgs/msg/BatterieStates`
**命令示例：** `ros2 topic echo /[namespace]/system/batteries/left`

## 查阅右电池信息
**功能概述：** 订阅Topic反馈左电池信息
**Topic：** `system/batteries/right`
**Msg Type：** `tita_system_msgs/msg/BatterieStates`
**命令示例：** `ros2 topic echo /[namespace]/system/batteries/right`

## 查阅超级电容信息
**功能概述：** 订阅Topic反馈超级电容信息
**Topic：** `system/batteries/super`
**Msg Type：** `tita_system_msgs/msg/BatterieStates`
**命令示例：** `ros2 topic echo /[namespace]/system/batteries/super`

## 查阅超级电容信息
**功能概述：** 订阅Topic反馈电源统计信息
**Topic：** `system/power_supply/info`
**Msg Type：** `tita_system_msgs/msg/PowerSupplyInfo`
**命令示例：** `ros2 topic echo /[namespace]/system/power_supply/info`
````{note}
修改文件 /usr/share/power_bridges/conf/tita_power.toml 中的 record_battery_info=1 #0关闭 1打开
````