# ORB2-RGBD on bandeja setup
The repo provides tools, scripts and configs to run ORB-SLAM2 on the Bandeja data (RGBD):
* RGB: smartphone back-camera (standard/wide-angle)
* Depth: Azure Kinect

Jupyter-notebook provides the next steps for data, extracted from rosbags:
1. Undistort **RGB image**
2. Create point cloud from **depth image**, transform it to RGB reference frame, project to RGB
3. Convert data to TUM format: associate RGB and depth timestampts, save in proper format (8-bit RGB, 16-bit depth with scale factor)  

## Setup
Build ORB-SLAM2 with patches
```console
git clone https://github.com/MobileRoboticsSkoltech/samsung-avatar-dataset-orb2.git
git submodule update --init --recursive
cd ORB_SLAM2
./build.sh
```

## Run
1. Use Jupyter-notebook to prepare data directory for ORB-SLAM2 in TUM format -- `<data-dir>`
2. Run ORB-SLAM2 with proper config (for standard or wide RGB-camera)
```console
ORB_SLAM2/Examples/RGB-D/rgbd_tum ORB_SLAM2/Vocabulary/ORBvoc.txt orb_bandeja_standard.yaml <data-dir> <data-dir>/association.txt
```
