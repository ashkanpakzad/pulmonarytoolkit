# Importing and loading data

As with many Dicom-based programs, getting data into PTK is a two-step process. You first **import** images into the PTK database. Then you can **load** any dataset from the database. Once imported, images remain in the database permanently (unless you delete them), and they are accessible from the sidebar or the Patient Browser. You can only have one dataset loaded at a time, but switching to a different dataset is fast due to PTK's smart caching.

## Importing data

The way Dicom images are stored on disk can be a mess - image stacks can be split across multiple folders and mixed in with image and non-image data. PTK simplifies the whole import process because you just need to specify a root directory. PTK will search for images recursively through all the subdirectories, ignoring all non-Dicom images, and will group all the images into patients and series based on the image metadata. PTK will group together series even if they are spread across multiple directories (this does happen!) However, all the images do need to be imported at the same time.

The easiest way to import data is to startup PTK
```
ptk
```
and then click the `+` (Import) button at the bottom left. Choose a root folder. PTK will recursively search for and import the data it finds. This could take some time if you have a lot of images. Once all the images have been found you will see the left sidebar populated with patient and series data.

You can also show the Patient Browser to see all the image series grouped by patient in a separate window.

## Loading data

You can load one dataset at a time. You can load any dataset that has been imported. You can either load from the sidebar, or from the Patient Browser.

### Using the sidebar

First click on the patient you want to load (scroll if necessary down the patient list). Then all the available series will be shown underneath. Click on a series to load that dataset.

### Using the Patient Browser
Click the Patient Browser button to show the Patient Browser if it is not already shown. Then scroll through all the series (grouped by patient) and click the series you wish to load. The left-hand sidebar is a shortcut to patients and scrolls the main panel to that patient.

## The first time you load a dataset

PTK does some initial processing of images the first time it loads a particular dataset. This is to identify the lung region of interest (ROI), and can take up to a minute or two depending on how large the dataset is. Identifying this ROI allows the non-lung regions to be internally discarded (the original data is not affected!) which substantially speeds up execution time and reduces memory usage. This ROI calculation is performed once per dataset the first time you load that dataset. Even if you restart PTK, restart Matlab or reboot your computer, it will not need to perform it again for that dataset.

## Switching between datasets

To switch to another dataset simply click on the series you wish to load in the sidebar or Patient Browser. If you are switching to a series you have not previously loaded then you may have to wait for the ROI computation. However, once this has been done switching between datasets is very fast and usually takes only a second or two.
