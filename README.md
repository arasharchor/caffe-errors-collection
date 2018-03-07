# caffe-errors-collection


# error:
AR -o .build_release/lib/libcaffe.a
LD -o .build_release/lib/libcaffe.so.1.0.0
/usr/bin/ld: cannot find -lhdf5_hl
/usr/bin/ld: cannot find -lhdf5
collect2: error: ld returned 1 exit status
Makefile:572: recipe for target '.build_release/lib/libcaffe.so.1.0.0' failed
make: *** [.build_release/lib/libcaffe.so.1.0.0] Error 1
make: *** Waiting for unfinished jobs....

# solution:
majid@majid:~/caffe$ cd /usr/lib/x86_64-linux-gnu/
majid@majid:/usr/lib/x86_64-linux-gnu$ sudo ln -s libhdf5_serial.so.10.1.0 libhdf5.so
majid@majid:/usr/lib/x86_64-linux-gnu$ sudo ln -s libhdf5_serial_hl.so.10.0.2 libhdf5_hl.so



# error
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:625: recipe for target '.build_release/tools/upgrade_net_proto_binary.bin' failed
make: *** [.build_release/tools/upgrade_net_proto_binary.bin] Error 1

# solution
uncomment OPENCV_VERSION := 3 in Makefile.config
