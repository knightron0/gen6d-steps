# Gen6D Setup & Run 

## Goals 
- Setup environment for COLMAP
- Setup environment for Gen6D
- Download all required data
- Load custom object in the model 
- Allow prediction commands


## Installation
1. Clone the Gen6D repository
```
git clone https://github.com/liuyuan-pal/Gen6D.git
```
2. Create a virtual environment with Python 3.6 using either pip/conda. Install all of the packages listed in `Gen6D/requirements.txt`.
3. Install [COLMAP](https://github.com/colmap/colmap/releases) for Windows. Note: make sure to install the CUDA version.
4. Download [pretrained models](https://connecthkuhk-my.sharepoint.com/personal/yuanly_connect_hku_hk/_layouts/15/onedrive.aspx?ga=1&id=%2Fpersonal%2Fyuanly%5Fconnect%5Fhku%5Fhk%2FDocuments%2FGen6D%2Fgen6d%5Fpretrain%2Etar%2Egz&parent=%2Fpersonal%2Fyuanly%5Fconnect%5Fhku%5Fhk%2FDocuments%2FGen6D). The file structure should look like:
```
Gen6D
|-- data
    |-- model
        |-- detector_pretrain
            |-- model_best.pth
        |-- selector_pretrain
            |-- model_best.pth
        |-- refiner_pretrain
            |-- model_best.pth
```
5. Create a sub-folder under `data` called `custom`. Create another folder inside `custom` called `flourbag`.
6. Download the point cloud file `object_point_cloud.ply` and meta info file `meta_info.txt`. Place it in the Gen6D folder like this:
```
Gen6D
|-- data
    |-- custom
       |-- flourbag
           |-- object_point_cloud.ply  # object point cloud
           |-- meta_info.txt           # meta information about z+/x+ directions
```
7. Download the `images` & `colmap` folders. Place them at the same level as the point cloud and meta info files.
```
Gen6D
|-- data
    |-- custom
       |-- flourbag
           |-- object_point_cloud.ply  # object point cloud
           |-- meta_info.txt           # meta information about z+/x+ directions
           |-- images                  # images
           |-- colmap                  # colmap project
```
8. Install `ffmpeg` from [here](https://ffmpeg.org/download.html).

## Prediction
1. Make sure the structure of the folder looks like this:
```
Gen6D
|-- data
    |-- custom
       |-- flourbag
           |-- object_point_cloud.ply  # object point cloud
           |-- meta_info.txt           # meta information about z+/x+ directions
           |-- images                  # images
           |-- colmap                  # colmap project
       |-- video                       # create this new folder
           |-- <test video>.mp4        # add your test videos in this folder
    |-- model
       |-- detector_pretrain
           |-- model_best.pth
       |-- selector_pretrain
           |-- model_best.pth
       |-- refiner_pretrain
           |-- model_best.pth
|-- configs
|-- train
... etc
```
Here are some test videos: [one](https://drive.google.com/file/d/1JKnF-5QEYT3pkxphOLmLf6sictPqqvLh/view?usp=sharing), [two](https://drive.google.com/file/d/1xPbDRDdQJ91d880f4CjgkjZZb-t8wuuP/view?usp=sharing).

2. Run the following command with the appropriate parameters.
```
python3 predict.py --cfg configs/gen6d_pretrain.yaml --database custom/flourbag  --video <path-to-video-mp4> --resolution 960 --transpose --output data/custom/flourbag/test --ffmpeg <path-to-ffmpeg-exe>
```
3. Find your output in `data/custom/flourbag/test/`!
