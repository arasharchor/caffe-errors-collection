#error
/home/majid/caffe2/caffe2/operators/conv_op_eigen.cc:24:2: error: #error "Caffe2 requires Eigen to be at least 3.3.0.";
 #error "Caffe2 requires Eigen to be at least 3.3.0.";
  ^
[ 56%] Building CXX object caffe2/CMakeFiles/caffe2.dir/operators/logit_op.cc.o
[ 57%] Building CXX object caffe2/CMakeFiles/caffe2.dir/operators/pack_segments.cc.o
[ 57%] Building CXX object caffe2/CMakeFiles/caffe2.dir/operators/free_op.cc.o
cc1plus: warning: unrecognized command line option ‘-Wno-invalid-partial-specialization’
caffe2/CMakeFiles/caffe2.dir/build.make:4070: recipe for target 'caffe2/CMakeFiles/caffe2.dir/operators/conv_op_eigen.cc.o' failed
make[2]: *** [caffe2/CMakeFiles/caffe2.dir/operators/conv_op_eigen.cc.o] Error 1
make[2]: *** Waiting for unfinished jobs....
CMakeFiles/Makefile2:2451: recipe for target 'caffe2/CMakeFiles/caffe2.dir/all' failed
make[1]: *** [caffe2/CMakeFiles/caffe2.dir/all] Error 2
Makefile:138: recipe for target 'all' failed

# Solution 
majid@majid:~/caffe2/build$ cat /usr/include/eigen3/Eigen/src/Core/util/Macros.h | grep VERSION
#define EIGEN_WORLD_VERSION 3
#define EIGEN_MAJOR_VERSION 2
#define EIGEN_MINOR_VERSION 92
#define EIGEN_VERSION_AT_LEAST(x,y,z) (EIGEN_WORLD_VERSION>x || (EIGEN_WORLD_VERSION>=x && \
                                      (EIGEN_MAJOR_VERSION>y || (EIGEN_MAJOR_VERSION>=y && \
                                                                 EIGEN_MINOR_VERSION>=z))))
#if defined(__CC_ARM) || defined(__ARMCC_VERSION)
#if (defined(__STDC_VERSION__) && (__STDC_VERSION__ >= 199901))       \
  || (defined(_LIBCPP_VERSION) && !defined(_MSC_VER))
majid@majid:~/caffe2/build$ sudo apt-get install eigen --upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eigen
majid@majid:~/caffe2/build$ sudo apt-get install eigensoft 
Display all 56346 possibilities? (y or n)
majid@majid:~/caffe2/build$ sudo apt-get install eigensoft 
Display all 56346 possibilities? (y or n)
majid@majid:~/caffe2/build$ cd 
majid@majid:~$ git clone https://github.com/eigenteam/eigen-git-mirror.git
Cloning into 'eigen-git-mirror'...
remote: Counting objects: 91102, done.
remote: Total 91102 (delta 0), reused 0 (delta 0), pack-reused 91102
Receiving objects: 100% (91102/91102), 91.34 MiB | 3.74 MiB/s, done.
Resolving deltas: 100% (69043/69043), done.
Checking connectivity... done.
majid@majid:/usr/include$ sudo mv /home/majid/eigen3 /usr/include/
majid@majid:/usr/include$ cat /usr/include/eigen3/Eigen/src/Core/util/Macros.h | grep VERSION
#define EIGEN_WORLD_VERSION 3
#define EIGEN_MAJOR_VERSION 3
#define EIGEN_MINOR_VERSION 90
#define EIGEN_VERSION_AT_LEAST(x,y,z) (EIGEN_WORLD_VERSION>x || (EIGEN_WORLD_VERSION>=x && \
                                      (EIGEN_MAJOR_VERSION>y || (EIGEN_MAJOR_VERSION>=y && \
                                                                 EIGEN_MINOR_VERSION>=z))))
#if defined(__CC_ARM) || defined(__ARMCC_VERSION)
    ((defined(__STDC_VERSION__) && (__STDC_VERSION__ >= 199901))       \
  || (defined(_LIBCPP_VERSION) && !defined(_MSC_VER)) \

