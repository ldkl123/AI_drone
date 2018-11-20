
시작 하기전에 아래 실행
sudo apt-get update
sudo apt-get upgrade

********************** drone_training errors 
hector_uav_msgs 를 필요로 하는데, include 에 넣어서 해도 안되서 그냥 catkin_ws에 패키지화해서 넣어버렸다.


********************** parrot_ardrones errors 
	
parrot_ardrones 를 catkin_ws/src 폴더 안에 통째로 넣어야한다.

/usr/include 폴더 안에 ignitions 파일이 있어야한다. 
 
sjtu_drone/launch 파일의 simple.launch가 핵심 launch 파일이다. 

gzserver 는 있는 그대로 하되, gzclient는 gazebo_ros 에 있는 gzclient 를 타입으로 두고 노드를 생성해야한다. 이유는 --verbose 에 있는 듯하다. 

Spwan quadrotor을 불러올때 있는 pkg="sjtu_drone"으로 설정하여 spawn_model을 불러오면 안된다. pkg="gazebo_ros" 로 수정하고, args="-sdf ... 을 사용하여 sjtu_drone 패키지 안의 sjtu_drone.sdf를 직접 사용하여야 한다.

sjtu_drone/models/sjtu_drone 에서 sjtu_drone.sdf 파일이 드론 형상을 만드는 중요한 파일이다. 파일 안에 <mesh> 부분에서 <uri>부분에 실제 모델링 파일을 찾는 경로를 입력해야하는데, model:// 로 시작해야하며, models 경로 다음 부터의 경로를 넣는다(models 와 model://은 상관관계가 있는 듯). 형상이 나오지 않으면 무조건 경로를 의심하자.
 
	
