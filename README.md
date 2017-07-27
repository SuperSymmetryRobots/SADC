# seat_car_simulator

Developed at **IRI**, Institut de Robòtica i Informàtica Industrial, CSIC-UPC:  
www.iri.upc.edu

Provides a Gazebo simulation of a scaled 1:10 vehicle:  
https://github.com/AutoModelCar/AutoModelCarWiki/wiki

Used in the SEAT Autonomous Driving Challenge:  
http://www.autonomousdrivingchallenge.com

## Installing


1. Clone AutoModelCar version-3 repo, because we need its odometry package
```
mkdir -p ~/seat
cd ~/seat
git clone -b version-3 https://github.com/AutoModelCar/model_car.git model_car_3
#git clone -b version-3-kinetic https://github.com/AutoModelCar/model_car.git model_car_3
source /opt/ros/indigo/setup.bash
#source /opt/ros/kinetic/setup.bash
cd ~/seat/model_car_3/catkin_ws
rm -rf build devel
# We actually only need the odometry package
catkin_make --only-pkg-with-deps odometry
```

2. Create our catkin_ws workspace, overlaying model_car_3/catkin_ws
```
source ~/seat/model_car_3/catkin_ws/devel/setup.bash
mkdir -p ~/seat/catkin_ws/src
cd ~/seat/catkin_ws
catkin_make
source ~/seat/catkin_ws/devel/setup.bash
# You can/should add this last line to you ~/.bashrc
```


3. Clone simulator in catkin_ws
```
roscd; cd ../src
git clone https://gitlab.iri.upc.edu/seat_adc/seat_car_simulator.git
rosdep install -i --from-paths seat_car_simulator
roscd; cd ..
catkin_make --only-pkg-with-deps seat_car_simulator
```

## Running 

```
roslaunch seat_car_gazebo sim.launch

# Test car movement
rostopic pub /manual_control/steering std_msgs/Int16 "data: 75"
rostopic pub /manual_control/speed    std_msgs/Int16 "data: -750"
```