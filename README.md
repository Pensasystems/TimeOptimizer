# TimeOptimizer
## 1.Introduction

TimeOptimizer is a tool to do **re-timing** (time optimization) of an **arbitrary** piecewise polynomial-based trajectory (no matter monomial polynomial, Bezier curve, B-spline or others). The objective of this work is to map the original parametrization variable to a new variable (time), with which the trajectory can finish as fast as possible and respect all kinodynamic limits (velocity, acceleration).
For details, we refer readers to our paper.

**Authors:**[Fei Gao](https://ustfei.com/) and [Shaojie Shen](http://www.ece.ust.hk/ece.php/profile/facultydetail/eeshaojie) from the [HUKST Aerial Robotics Group](uav.ust.hk).

**Disclaimer**

This is a research repo, any fitness for a particular purpose is disclaimed.

**Related Paper**
* **Optimal Time Allocation for Quadrotor Trajectory Generation,** Fei Gao, William Wu, Jie Pan, Boyu Zhou and Shaojie Shen, IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2018, Madrid, Spain.
[full text](https://ecefeigao.files.wordpress.com/2018/08/iros2018fei.pdf)

Video of this paper can be found at:

<a href="https://www.youtube.com/watch?v=YJdwyJ5h8Ac" target="_blank"><img src="https://img.youtube.com/vi/YJdwyJ5h8Ac/0.jpg" 
alt="video" width="405" height="270" border="10" /></a>


If you use this planning framework for your academic research, please cite our related paper.
```
@inproceedings{Fei2018IROS,
    Address = {Madrid, Spain},
    Author = {F. Gao and W.Wu and J. Pan and B. Zhou and S. Shen},
    Booktitle = {Optimal Time Allocation for Quadrotor Trajectory Generation},
    Title = {Proc. of the {IEEE/RSJ} Intl. Conf. on Intell. Robots and Syst.({IROS})},
    Month = Oct,
    Year = {2018}}
}
```
**Implementation**

## 2.Prerequisities
- Our testing environment: **Ubuntu** 16.04, **ROS** Kinetic.
- If you want to directly set waypoints in **Rviz** for generating the spatial trajectory, please follow **5.2**. Otherwise you should follow **5.1**. 
- Remember to approve a license from **mosek** following **4**.

## 3.Build on ROS
  Clone the repository to your catkin workspace and catkin_make. For example:
```
  cd ~/catkin_ws/src
  git clone https://github.com/HKUST-Aerial-Robotics/TimeOptimizer.git
  cd ../
  catkin_make
  source ~/catkin_ws/devel/setup.bash
```

## 4.Install Mosek
We use **mosek** for solving second-order cone program(SOCP). To use mosek, you should approve an academic license in [here](https://www.mosek.com/products/academic-licenses/). The academic license is free and is easy to approve. Then create a folder named 'mosek' in your home directory and put your license in it. All header and library files are already included in the 'third_party' folder under this repo, so you don't need to download mosek again. 

## 5.Usage
The time optimizer can be applied to an arbitrary type pieciwise polynomial-based trajectory, and we proovide a simple demo using minimum-jerk monomial polynomials as an example. If you have done all above configuration, you can try the simple demo in two ways

**1.**
We provide a clean launch file which has no dependence on other packages, suppose you do not want to configure the interactive tools we provide. In this way, you can write down you the coordinates of all waypoints in the **traj.json** file under the root directory of this package, and the program would read it after launching:
```
  roslaunch time_optimizer clean_demo.launch
```

<img src="fig/example1.gif" alt="example1" width = "750" height = "450">


## 6.Extension
To use the time optimizer with other kinds of spatial trajectory generator, you can follow 'demo.cpp' as an example. The simplest way is to implemente your own trajectory type as an inheritance of the class 'Trajectory' definded in 'trajectory_base.h'.

## 7.Acknowledgements
  We use [ecos](https://github.com/embotech/ecos) for solving second-order cone program(SOCP).

## 8.Licence
The source code is released under [GPLv3](http://www.gnu.org/licenses/) license.

## 9.Notes
- The code has not been deeply tested, if you find any problems, do not hesitate to raise an issue or write an e-mail to me.
