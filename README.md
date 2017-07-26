# seat_car_simulator

Developed at **IRI**, Institut de Robòtica i Informàtica Industrial, CSIC-UPC:  
www.iri.upc.edu

Provides a Gazebo simulation of a scaled 1:10 vehicle:  
https://github.com/AutoModelCar/AutoModelCarWiki/wiki

Used in the SEAT Autonomous Driving Challenge:  
http://www.autonomousdrivingchallenge.com

## Installing

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
```