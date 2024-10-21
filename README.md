# Neural Networks for Learning Coherent Features in Point Clouds

### Installation
1.  Clone repository
2.  Install Tensorflow 1.9.0 GPU with CUDA 9.0 and Python 3.6 (newer versions are not supported!)  
    `conda create -n tc python=3.6`  
    `conda activate tc`  
    `pip install tensorflow-gpu==1.9.0`
3.  Build the required TF tools  
    `cd neuralparticles/tensorflow; make`
4.  Install requirements with pip  
    `pip install matplotlib keras==2.2.4`

### Generate Data (Optional)
1.  Build Mantaflow:  
    `mkdir neuralparticles/build; cd neuralparticles/build`  
    `cmake .. -DNUMPY=ON -DPYTHON_LIBRARY="ENV_PATH/lib/libpython3.6m.dylib" -DPYTHON_INCLUDE_DIRS="ENV_PATH/include/python3.6m"`  
    *(specify python library and include if necessary)*   
    `make -j4`  
    *for more information: http://mantaflow.com*
2.  Generate ground-truth data:  
    **2D Data**: `python -m gen_ref config config/ours.txt data 2D_data/`  
    **3D Data**: `python -m gen_ref config config_3d/ours.txt data 3D_data/`
3.  Generate source data (ground-truth required!):  
    **2D Data**: `python -m gen_src config config/ours.txt data 2D_data/`  
    **3D Data**: `python -m gen_src config config_3d/ours.txt data 3D_data/`
4.  Generate test data:  
    **2D Data**: `python -m gen_real config config/ours.txt data 2D_data/`  
    **3D Data**: `python -m gen_real config config_3d/ours.txt data 3D_data/`

### Download Data (Alternative)
**2D Data**: https://syncandshare.lrz.de/getlink/fi9n8JVoJtPMu497cdvXYCVG/2D_data  
**3D Data**: https://syncandshare.lrz.de/getlink/fiWCVA4sEr4w1yMg4nD5Bs5Z/3D_data

### Run Training
**2D Data**: `python -m train config config/ours.txt data 2D_data/`  
**3D Data**: `python -m train config config_3d/ours.txt data 3D_data/`

### Run Inference
**2D Data**: `python -m run config config/ours.txt data 2D_data/ real 1`  
**3D Data**: `python -m run config config_3d/ours.txt data 3D_data/ real 1`  

*Additional 3D tests (3D data required!):* 

**Spider Mesh Data**
*   Download data: https://syncandshare.lrz.de/getlink/fiT622EgC5rC34KC9DQXfDAV/spider_data
*   Run inference: `python -m run_mesh config config_3d/ours.txt data 3D_data/ test spider_data/ res 200`
 
**Walking Man Mesh Data**
*   Download data: https://syncandshare.lrz.de/getlink/fiTbE56WpRWPSFD4cUSVxwxL/man_data
*   Run inference: `python -m run_mesh config config_3d/ours.txt data 3D_data/ test man_data/ res 200`

