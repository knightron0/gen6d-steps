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
2. Install [COLMAP](https://github.com/colmap/colmap/releases) for Windows. Note: make sure to install the CUDA version.
3. Download [pretrained models](https://connecthkuhk-my.sharepoint.com/personal/yuanly_connect_hku_hk/_layouts/15/onedrive.aspx?ga=1&id=%2Fpersonal%2Fyuanly%5Fconnect%5Fhku%5Fhk%2FDocuments%2FGen6D%2Fgen6d%5Fpretrain%2Etar%2Egz&parent=%2Fpersonal%2Fyuanly%5Fconnect%5Fhku%5Fhk%2FDocuments%2FGen6D). The file structure should look like:
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
4. Create a sub-folder under `data` called `custom`. Create another folder inside `custom` called `flourbag`.
5. Download the point cloud file `object_point_cloud.ply` and meta info file `meta_info.txt`. Place it in the Gen6D folder like this:
```
Gen6D
|-- data
    |-- custom
       |-- flourbag
           |-- object_point_cloud.ply  # object point cloud
           |-- meta_info.txt           # meta information about z+/x+ directions
```
6. Download the `images` & `colmap` folders. Place them at the same level as the point cloud and meta info files.
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
