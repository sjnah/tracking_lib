# tracking_lib
　　The LiDAR tracking library, for tracking objects obtaining from segmentation-based detection and improve segmentation.
<p align="center">
    <img src=".readme/demo1.gif" width="720px" alt=""/>
    <img src=".readme/demo2.gif" width="720px" alt=""/>
</p>

## How to use
1. We name your ros workspace as `CATKIN_WS` and `git clone` as a ROS package.
    ```bash
    $ cd $(CATKIN_WS)
    # we recommand you to organize your workspace as following
    $ mkdir -p src/perception/libs

    # git clone basic common libraries
    $ cd $(CATKIN_WS)/src/
    $ git clone https://github.com/LidarPerception/common_lib.git common

    # git clone perception libraries, tracking_lib and its dependencies
    $ cd $(CATKIN_WS)/src/perception/libs
    $ git clone https://github.com/sjnah/roi_filters_lib.git roi_filters
    $ git clone https://github.com/LidarPerception/object_builders_lib.git object_builders
    $ git clone https://github.com/sjnah/segmenters_lib.git segmenters
    $ git clone https://github.com/LidarPerception/feature_extractors_lib.git feature_extractors
    $ git clone https://github.com/sjnah/tracking_lib.git tracking

    # build your ros workspace for our Tracking-help segmentation demo
    $ cd $(CATKIN_WS)
    $ catkin_make -DCMAKE_BUILD_TYPE=Release
    ```
    ```bash
    $ cd $(CATKIN_WS)
    $ roslaunch tracking_lib demo_real.launch
    ```

## [Parameters](./launch/demo.launch)
　*detection.yaml* and *tracking.yaml* configure the detection_node and tracking_node in sample. *kitti/\*.yaml* configure the algorithm parameters for KiTTI Dataset, *Segmenter.yaml* and *TrackingWorker.yaml* separately for **Seg-based Segmentation**, **Tracking**.
```bash
./config
├── detection.yaml
├── kitti
│   ├── Segmenter.yaml
│   └── TrackingWorker.yaml
└── tracking.yaml
```

## TODO lists
### Non-ground Segmenters
- [x] **Tracking-help Segmentation**. IV, 2012. A basic implementation in [tracking_node](./samples/tracking_node.cpp)
    ```bibtex
    @inproceedings{himmelsbach2012tracking,
      title={Tracking and classification of arbitrary objects with bottom-up/top-down detection},
      author={Himmelsbach, Michael and Wuensche, H-J},
      booktitle={Intelligent Vehicles Symposium (IV), 2012 IEEE},
      pages={577--582},
      year={2012},
      organization={IEEE}
    }
    ```
    <p align="center">
        <img src=".readme/Tracking-help Segmentation.png" width="480px" alt=""/>
    </p>
