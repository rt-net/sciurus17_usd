# sciurus17_usd
Isaac Sim向けにセットアップしたSciurus17のUSDファイル用リポジトリです。

## Table of Contents
- [sciurus17_usd](#sciurus17_usd)
  - [Requirements](#requirements)
  - [Installation](#installation)
    - [Clone USD Repository](#clone-usd-repository)
    - [ROS 2 Dependencies Setup (Optional)](#ros-2-dependencies-setup-optional)
  - [How to Use](#how-to-use)
    - [Load the Model](#load-the-model)
    - [Run ROS 2 Examples](#run-ros-2-examples)
  - [USD Files](#usd-files)
  - [Proprietary Rights](#proprietary-rights)

## Requirements

- OS
  - Ubuntu 24.04
- Isaac Sim
    - 5.1.0
- ROS 2 (Optional)
  - [Jazzy Jalisco](https://docs.ros.org/en/jazzy/Installation.html)

## Installation

### Clone USD Repository
```bash
git clone https://github.com/rt-net/sciurus17_usd.git
```

### ROS 2 Dependencies Setup (Optional)
ROS 2と連携させる場合は下記の手順で依存パッケージをインストールします。  

```bash
# Create workspace directory
mkdir -p ~/ros2_ws/src && cd ~/ros2_ws/src

# Clone package
git clone -b $ROS_DISTRO https://github.com/rt-net/sciurus17_ros.git
git clone -b $ROS_DISTRO https://github.com/rt-net/sciurus17_description.git
git clone -b 0.3.0 https://github.com/PickNikRobotics/topic_based_ros2_control.git

# Install dependencies
rosdep install -r -y -i --from-paths .

# Build & Install
cd ~/ros2_ws
colcon build --symlink-install
source ~/ros2_ws/install/setup.bash
```

## How to Use

### Load the Model
1. Isaac Simを起動します
2. sciurus17.usdを開きます

### Run ROS 2 Examples
1. Isaac Simを起動します
2. sciurus17_ros2_with_cube.usdを開きます
3. Isaac SimでシミュレーションのPlayボタンを押します
4. 下記コマンドを実行してSciurus17のROS 2ノードを起動します

```sh
ros2 launch sciurus17_examples demo.launch.py use_head_camera:=false use_chest_camera:=false use_isaacsim:=true use_sim_time:=true
```

5. 例として右手でピックアンドプレースを行うサンプルを実行します

```sh
ros2 launch sciurus17_examples example.launch.py example:='pick_and_place_right_arm_waist' use_sim_time:=true
```

Sciurus17のサンプルについては [rt-net/sciurus17_ros](https://github.com/rt-net/sciurus17_ros/tree/ros2/sciurus17_examples) をご参照ください。

## USD Files
- sciurus17.usd: Sciurus17のロボットモデル単体のUSDです
- sciurus17_ros2.usd: sciurus17.usdにROS 2連携の設定を追加したUSDです
- sciurus17_ros2_with_cube.usd: sciurus17_ros2.usdにROS 2サンプル用のcube等を追加したUSDです

## Proprietary Rights
Sciurus17は、アールティが開発した研究用上半身ロボットです。
本リポジトリのデータ等に関するライセンスについては、[LICENSE](./LICENSE)ファイルをご参照ください。
企業による使用については、自社内において研究開発をする目的に限り、本データの使用を許諾します。
本データを使って自作されたい方は、義務ではありませんが弊社ロボットショップで部品をお買い求めいただければ、励みになります。
商業目的をもって本データを使用する場合は、商業用使用許諾の条件等について弊社までお問合せください。

サーボモータのXM540やXM430に関するCADモデルの使用については、ROBOTIS社より使用許諾を受けています。
Sciurus17に使用されているROBOTIS社の部品類にかかる著作権、商標権、その他の知的財産権は、ROBOTIS社に帰属します。
