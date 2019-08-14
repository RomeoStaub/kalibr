##Calibration with Kalibr


RUN from this folder. "calibration_results"
cd /home/romeo/catkin_ws/src/kalibr/calibration/calibration_results
Steady cam - move april-grid in front of camera

Run calibration for camera intrinsics:


rosrun kalibr kalibr_calibrate_cameras --bag ../static/static.bag --topics /blackfly/image_raw --models pinhole-equi --target ../config/april_6x6.yaml --show-extraction 

rosrun kalibr kalibr_calibrate_cameras --bag ../static/static.bag --topics /blackfly/image_raw --models pinhole-equi --target ../config/april_6x6_asl.yaml --show-extraction 

rosrun kalibr kalibr_calibrate_cameras --bag ../dynamic/dynamic_02.bag --topics /blackfly/image_raw --models pinhole-radtan --target ../config/april_6x6.yaml --show-extraction 

optional change baglength with the following command 
--bag-from-to 5 100

use following command for more options
rosrun kalibr kalibr_calibrate_cameras --h



camera to imu calibration (run in calibration_results folder ):

kalibr_calibrate_imu_camera --bag MYROSBAG.bag --cam camchain.yaml --imu imu.yaml \
             --target aprilgrid.yaml


kalibr_calibrate_imu_camera --target ../config/april_6x6.yaml --cam camchain-..staticstatic.yaml --imu ../config/xsens_mti100.yaml --bag ../dynamic/dynamic_02.bag  --show-extraction



Create rovio.info

cd /home/romeo/catkin_ws/src/kalibr/aslam_offline_calibration/kalibr/python/exporters


Calibration validator
cd /home/romeo/catkin_ws/src/kalibr/calibration
terminal 1:
rosbag play dynamic/dynamic.bag

terminal 2:
python kalibr_camera_validator --target 	/home/romeo/catkin_ws/src/kalibr/calibration/config/april_6x6.yaml --cam /home/romeo/catkin_ws/src/kalibr/calibration/calibration_results/camchain-..staticstatic.yaml





