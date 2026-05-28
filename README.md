# JAKA-robot-grasping-V2

## Project Demo

![Demo](anygrasp.gif)

#### Description
JAKA robot grasping system using deep learning for object detection and grasp planning.

#### Software Architecture

The system consists of the following main components:

- **JAKA Robot Control**: Interfaces with JAKA robot via TCP/IP for motion control and gripper operations
- **RealSense Camera**: Intel RealSense depth camera for RGB-D image acquisition
- **Grasp Detection**: Deep learning model (GraspNet) for generating grasp proposals from point clouds
- **Point Cloud Processing**: PointNet2-based neural network for 3D point cloud analysis
- **Collision Detection**: Model-free collision detection for safe grasp planning
- **Coordinate Transformation**: Camera-to-robot coordinate system transformation

**Key Modules:**
- `main.py`: Main control loop and command-line interface
- `GraspInit.py`: Camera and grasp detection initialization
- `jaka.py`: JAKA robot SDK wrapper
- `GVF.py`: Grasp visualization functions
- `models/`: Deep learning model implementations
- `pointnet2/`: PointNet2 CUDA operations
- `utils/`: Utility functions for data processing

#### Installation

**Prerequisites:**
- Python 3.7+
- JAKA Robot (with SDK)
- Intel RealSense D435/D455 camera
- CUDA-capable GPU (for PointNet2)

**Steps:**

1. Clone the repository
```bash
git clone https://github.com/jackgong666/robot-anygrasp.git
cd robot-anygrasp
```

2. Install Python dependencies
```bash
pip install pyrealsense2 numpy opencv-python torch torchvision
```

3. Install PointNet2 CUDA extensions
```bash
cd pointnet2
python setup.py install
cd ..
```

4. Install KNN module
```bash
cd knn
python setup.py install
cd ..
```

5. Configure robot IP address
Edit `config.json` and set your robot's IP address:
```json
"IPaddress": "192.168.15.106"
```

#### Instructions

**1. Start the system:**
```bash
python main.py
```

**2. Available commands:**
- `help` or `?`: Show all available commands
- `cap [num]`: Capture image and detect grasps (num: number of grasp proposals)
- `orbit`: Start continuous grasping loop
- `orbit_manu [num]`: Grasp specified number of objects
- `gh`: Move robot to home position
- `gb`: Move robot to basket position
- `go [arg]`: Open gripper
- `gc [arg]`: Close gripper
- `gp`: Print current joint positions
- `sh`: Set current position as home
- `sb`: Set current position as basket
- `exit`: Exit the program

**3. Workflow:**
1. Run `python main.py` to start
2. Robot automatically moves to home position
3. System enters automatic grasping loop
4. Camera captures RGB-D images
5. Grasp detection generates proposals
6. Robot executes grasp and places object in basket
7. Process repeats

#### Contributors

- Jack Gong
- Xiaofeng Du

#### Contribution

1.  Fork the repository
2.  Create Feat_xxx branch
3.  Commit your code
4.  Create Pull Request


#### Gitee Feature

1.  You can use Readme\_XXX.md to support different languages, such as Readme\_en.md, Readme\_zh.md
2.  Gitee blog [blog.gitee.com](https://blog.gitee.com)
3.  Explore open source project [https://gitee.com/explore](https://gitee.com/explore)
4.  The most valuable open source project [GVP](https://gitee.com/gvp)
5.  The manual of Gitee [https://gitee.com/help](https://gitee.com/help)
6.  The most popular members  [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
