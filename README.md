# Jenkins Setup For ROS
Tutorial for running ROS test in jenkins and how to setup.

## Download 2 docker images

```
docker pull ros:melodic-ros-base
docker pull jenkins/jenkins:lts
```

## Start Jenkins using Docker

```
docker run --name jenkins -u root -p 8080:8080 -v $(which docker):/usr/bin/docker -v /var/run/docker.sock:/var/run/docker.sock jenkins/jenkins:lts
```

> Remember the password for future login, you will see something in terminal:
```
Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

483d1d6cd3de49db86f76efae8d8fd5f

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword
```

> open browser and go to localhost:8080
* intall suggested pkgs and wait finish


> go to Manage Jenkins-->Manage Plugins-->Available--> search docker
```
install following
    --> Docker
    --> Docker Commons
    --> Docker Pipeline
    --> docker-build-step 
    --> Docker Compose Build Step 
    --> Docker API 
    
then click install without restart
```
> add Jenkins file
* See Jenkins file in this repo as example, we can add mutiple test, parallel test, etc... 
* In this Jenkins file, test 2 parts. first test package can be compiled or not. second test parallel testing only print AA and BB 

### Start Jenkins test(link to public repository)
>Setup testing link to public repository 
<img src="https://github.com/tsengapola/my_image_repo/blob/main/jenkins_ros/add_repo.gif" width="500" height="300"/>

### Start Jenkins test(link to private repository)
> go to your github: setting->Developer settings ->Personal access tokens ,then click Generate new token and record token number 
> 
> different part setting as below:
> 
*  At item 'Branch Source',click Add,choose your test name 
<img src="https://github.com/pstsengb/Image_for_repository/blob/main/jenkin_use/Add.png" width="500" height="300"/>

*  Enter 'user name' and 'Password' ,which password is token number
<img src="https://github.com/pstsengb/Image_for_repository/blob/main/jenkin_use/enteruserandpassword.png" width="500" height="300"/>

*  when you finish operation as above,you will see Credential ,which can be selected,then select setting you have done
<img src="https://github.com/pstsengb/Image_for_repository/blob/main/jenkin_use/chosesetting.png" width="500" height="300"/>

> after Credential setting ok,rest parts same with Start Jenkins test(link to public repository)
> 


