## 一、reallab_eio+vio+evio算法运行步骤

#### 1、source

```
source ~/Workspace/uslam_ws/devel/setup.bash
```

#### 2、切换到.sh文件路径下

```
cd ~/Workspace/uslam_ws/src/rpg_ultimate_slam_open/applications/ze_vio_ceres/launch
```

#### 3、运行算法

A、EIO算法(event+IMU)

```
./live_eio.sh
```

**注：**EIO算法的关键文件为live_reallab_events_only.launch；可以修改的参数主要有frame_size、data_interval_between_event_packets、data_size_augmented_event_packet、noise_event_rate

B、VIO算法(image+IMU)

```
./live_vio.sh
```

**注：**VIO算法的关键文件为live_reallab_image_only.launch；其余同上

C、EVIO算法(event+image+IMU)

```
./live_evio.sh
```

**注：**EVIO算法的关键文件为live_reallab.launch；其余同上

#### 4、保存轨迹

A、在对应算法的launch文件中设置“轨迹输出”（以上三种算法已默认自动输出轨迹）

B、保存的轨迹文件(.csv)路径为：

```
~/Workspace/uslam_ws/src/rpg_ultimate_slam_open/data/traj_es.csv
```

**注：**每次运行算法，输出的轨迹文件会被覆盖，若要保存轨迹文件，需自行提前拷贝到其余地方。

#### 5、轨迹评估

主要是对在数据集上估计的轨迹进行评估，此部分命令参考文件note for experiments.md

## 二、在公开数据集上测试算法

#### 1、source

同上

#### 2、EIO

```
默认launch文件中的数据集：roslaunch ze_vio_ceres ijrr17_events_only.launch 
指定数据集：roslaunch ze_vio_ceres ijrr17_events_only.launch bag_filename:=xxx.bag
```

#### 3、VIO

```
默认launch文件中的数据集：roslaunch ze_vio_ceres ijrr17_image_only.launch 
指定数据集：roslaunch ze_vio_ceres ijrr17_image_only.launch bag_filename:=xxx.bag
```

#### 4、EVIO

```
默认launch文件中的数据集：roslaunch ze_vio_ceres ijrr17.launch 
指定数据集：roslaunch ze_vio_ceres ijrr17.launch bag_filename:=xxx.bag
```

**注：**不同的数据集序列要求参数不同，具体参数可以参考文件note for experiments.md

------

<div align="center">written by Wynelio on Jun 11, 2023.</div>



