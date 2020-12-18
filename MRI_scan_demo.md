# MRI Image Analysis

> When viewing an injury through imaging technology like MRI, it is useful to view the injury in multiple slices of the data to get a more representative view of the damage within areas of interest.


```python
#coding packages
import numpy as np
import pandas as pd
import glob
import matplotlib.pyplot as plt
import imageio
```

**Glob.glob function** can read in multiple files into python and allows you to apply processes over all of the contents within that file for data manipulation.
The function will locate all elements within the specified location (i.e. MRI_images folder), returning a list of all the file names that match a specified pattern in the file name parameter (asterisk.asterisk) in the directed file location. A asterisk is a wild card, where in this case, it will retrieve file names that follow the pattern: something.something, which is consistent with every file name in the folder.
> glob.glob('folder_name/subfolder_name/file_name')




```python
file_list = glob.glob('MRI_images/*.*') #directing glob function to MRI_images file
file_list #returned list of all file names in file location
```




    ['MRI_images/Img0012.jpg',
     'MRI_images/Img0015.jpg',
     'MRI_images/Img0020.jpg',
     'MRI_images/Img0004.jpg',
     'MRI_images/Img0003.jpg',
     'MRI_images/Img0014.jpg',
     'MRI_images/Img0013.jpg',
     'MRI_images/Img0002.jpg',
     'MRI_images/Img0005.jpg',
     'MRI_images/Img0006.jpg',
     'MRI_images/Img0001.jpg',
     'MRI_images/Img0008.jpg',
     'MRI_images/Img0019.jpg',
     'MRI_images/Img0010.jpg',
     'MRI_images/Img0017.jpg',
     'MRI_images/Img0009.jpg',
     'MRI_images/Img0007.jpg',
     'MRI_images/Img0016.jpg',
     'MRI_images/Img0011.jpg',
     'MRI_images/Img0018.jpg']



Can **sort** the list of file names so that all of the cross-section slices will be displayed in order (in this case in order the order they are seen in the spine):


```python
file_list = sorted(file_list) #reorganizing list names by cross-section number
file_list
```




    ['MRI_images/Img0001.jpg',
     'MRI_images/Img0002.jpg',
     'MRI_images/Img0003.jpg',
     'MRI_images/Img0004.jpg',
     'MRI_images/Img0005.jpg',
     'MRI_images/Img0006.jpg',
     'MRI_images/Img0007.jpg',
     'MRI_images/Img0008.jpg',
     'MRI_images/Img0009.jpg',
     'MRI_images/Img0010.jpg',
     'MRI_images/Img0011.jpg',
     'MRI_images/Img0012.jpg',
     'MRI_images/Img0013.jpg',
     'MRI_images/Img0014.jpg',
     'MRI_images/Img0015.jpg',
     'MRI_images/Img0016.jpg',
     'MRI_images/Img0017.jpg',
     'MRI_images/Img0018.jpg',
     'MRI_images/Img0019.jpg',
     'MRI_images/Img0020.jpg']



Creating an empty list of nested arrays where each index within the list will be one MRI image slice. To create the nested arrays that will be read by .imshow() we can iterate through each file in the sorted list, reading and saving the nested arrays coding for each slice with imageio.imread(). Create list of nested arrays by appending them into the previously created empty list.


```python
scans = [] #empty list
for filename in file_list:
    img = imageio.imread(filename)
    scans.append(img) #appending 'img' nested arrays into empty list
```


```python
len(scans) #checking the length of the list
```




    20




```python
scans[0].shape #to check the dimensions of the first arrays in the list of image arrays
```




    (256, 256, 3)



Can make subplots to visualize all of the slices in the spinal column assigning a title to label each slice:


```python
ind=0
# loop through each slice indexes
subplot_counter =1
fig=plt.figure(figsize=[10, 10])
for im in scans:
    ax= fig.add_subplot(4,5, subplot_counter)
    subplot_counter += 1
    for i in range(0,subplot_counter,1):
        ind = 0 + i
        ax.set_title('slice %d' % ind)
    ax.imshow(im)
    ax.axis('off')
    plt.tight_layout()
plt.show()
```




    
![png](MRI_scan_demo_files/MRI_scan_demo_11_0.png)
    



**Re-slicing** allows the image data to be viewed from a different perspective. This is done by stacking the 2D images to create a 3D volume of the spine and take an alternate slice of the data.


```python
vol = np.stack(scans) #stacking 2D images to create 3D volume of cross-section
```


```python
vol.shape
```




    (20, 256, 256, 3)




```python
fig=plt.figure(figsize=[9,15])
#slicing the coronal plane of the lumbar spinal column in grayscale
plt.imshow(vol[:,120,:,:], cmap='gray')
plt.axis('off')
plt.show()
```




    
![png](MRI_scan_demo_files/MRI_scan_demo_15_0.png)
    




```python

```
