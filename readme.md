1. pull docker
    
    `docker pull tensorflow/tensorflow:1.12.0-gpu`
    
2. start docker
    
    `docker run -it tensorflow/tensorflow:1.12.0-gpu /bin/bash`

3. install libs on ubuntu
    
        apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler -y
        apt-get install --no-install-recommends libboost-all-dev -y
        apt-get install apt-get install cuda-cublas-dev-9-0 -y
        apt-get install libopenblas-dev -y
        apt-get install python-dev
        apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev -y
        apt-get install python-opencv -y
        pip install scikit-image

4. copy ./Makefile.config to {PATH_TO_DORN}/DORN/caffe/
    
    `cp ./Makefile.config $PATH_TO_DORN/DORN/caffe/`

5. make soft link of lib*.so
    
       ln -sv  /usr/lib/x86_64-linux-gnu/libhdf5_serial.so /usr/lib/x86_64-linux-gnu/libhdf5.so
       ln -sv  /usr/lib/x86_64-linux-gnu/libhdf5_serial_hl.so /usr/lib/x86_64-linux-gnu/libhdf5_hl.so

6. make caffe
    
        cd $PATH_TO_DORN/DORN/caffe/
        make all
        make test
        make runtest

7. export caffe/python to PYTHONPATH
    
        export PYTHONPATH = $PATH_TO_DORN/DORN/caffe/python

8. Download KITTI pretrained model from https://github.com/hufu6371/DORN, put model into `$PATH_TO_DORN/DORN/models/`
    
9. Run KITTI demo. Comment the GPU mode code. See `./demo_kitti.py` in this repo, line 11 and line 12
        
        cd $PATH_TO_DORN/DORN/
        python demo_kitti.py --filename=./data/KITTI/demo_01.png --outputroot=./result/KITTI/
   
   check result in  `./result/KITTI`