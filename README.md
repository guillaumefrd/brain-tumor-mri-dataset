# brain-tumor-mri-dataset
Utilities to:
- download (using a few command lines) an MRI brain tumor dataset providing 2D slices, tumor masks and tumor classes.
- load the dataset in Python.

The dataset can be used for different tasks like image classification, object detection or semantic / instance segmentation. 

It was originally published [here](https://figshare.com/articles/brain_tumor_dataset/1512427) in Matlab v7.3 format.

3064 T1-weighted contrast-inhanced images with three kinds of brain tumor are provided.

![dataset-overview](https://github.com/guillaumefrd/brain-tumor-mri-dataset/blob/master/images/slices_example.png?raw=true)

### Download the dataset

```console
# create a directory
mkdir brain_tumor_dataset
cd brain_tumor_dataset

# download the dataset
wget https://ndownloader.figshare.com/articles/1512427/versions/5

# unzip the dataset and delete the zip
unzip 5 && rm 5

# concatenate the multiple zipped data in a single zip
cat brainTumorDataPublic_* > brainTumorDataPublic_temp.zip
zip -FF brainTumorDataPublic_temp.zip --out data.zip

# remove the temporary files
rm brainTumorDataPublic_*

# unzip the full archive and delete it 
unzip data.zip -d data && rm data.zip

# check that "data" contains 3064 files
ls data | wc -l
```

### Load the dataset with Python

##### Requirements
```
- numpy
- cv2
- hdf5storage
```

##### Usage
Execute the script [matlab_to_numpy.py](https://github.com/guillaumefrd/brain-tumor-mri-dataset/blob/master/matlab_to_numpy.py) with the dataset path as parameter. 

```bash
python matlab_to_numpy.py ~/brain_tumor_dataset
```
Optional: set the image dimension with `--image-dimension` or `-d` (default is 512).

### References

```
@article{Cheng2017,
author = "Jun Cheng",
title = "{brain tumor dataset}",
year = "2017",
month = "4",
url = "https://figshare.com/articles/brain_tumor_dataset/1512427",
doi = "10.6084/m9.figshare.1512427.v5"
}
```
