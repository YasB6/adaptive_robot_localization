# adaptive_robot_localization
 ROS package robot_localization revisited

This is the the hole robot_localization created package by Tom Moore, where some files were modified to compute the measurement noise covariance matrix online, according to the paper by in Isambi S. Mbalawata, Simo Sarkkab, Matti Vihola, Heikki Haario, 2015, "Adaptive Metropolis Algorithm Using Variational Bayesian Adaptive Kalman Filter", Algorithm 1 VB-AKF (Variational Bayesian Adaptive Kalman filter).

List of the modified files (w. r. t. the original files of the robot_localization):
=======================================================

src/ekf.cpp
src/filter_base.cpp
include/robot_localization/filter_base.h

New variables :
===========

*in filter_base.h :
____________

  // Adaptive measurement noise covariance matrix:
MeasurementCovariance_;
  // Parameters of the adaptive measurement noise covariance matrix:
B_ (matrix n x n)
nu_ (positive integer scalar)
  // Forgetting factor of the previous estimates of the covariance matrix:
RHO = 0.95; // Choose 0 < RHO<=1; set RHO = 1 for stationary measurement covariance matrix
  // Number of iterations of the recalculation of the measurement covariance matrix, at each time step:
N_ITERATIONS = 5;

*in ekf.cpp:
_________

stateSubset0;                            
measurementCovarianceSubset;
measurementCovarianceSubset0; 
innovationSubset0;                      
state0_;   



The original package  : robot_localization
==============================

robot_localization is a package of nonlinear state estimation nodes. The package was developed by Charles River Analytics, Inc.

Please see documentation here: http://docs.ros.org/melodic/api/robot_localization/html/index.html


