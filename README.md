# Roman Art Analysis

The work done focuses on analysis of the images of ancient roman statues for their social values.
This project contains parts as follow:

1. webpage parsers for data collecting from art databases

2. simple annotation tool for roman statue images

3. roman statue face extraction

4. face frontalization

5. Data Augmentation

6. Wrinkle analysis on forehead using Soft computing and algorithms


## Webpage Parsers for data Collectiion from Art Databases

The HTMLParser and state machine is used for parsing the webpages of the databases and downloading images and meta-data.

#### Related Code:

/Data_collection/downloader4MCLcamacuk.py: parsing the webpage 'http://museum.classics.cam.ac.uk/collections/casts' and download the images.
The dataset made can be seen in /dataset 

#### Deployment instructions:

Go to Data collection and run : python downloader4MCLcamacuk.py Path_to_save_data Page_begin Page_end

Extracts data from page 'Page_begin' to 'Page_end'
/dataset contains data from page 1 to page 3

## Simple Annotator for Roman Statue Images

An OpenCV high-gui based simple image annotation tool. This tool is used to annotate a set of images with a variable. The possible value of the variable can be two or more. The annotation results will be stored in a text file.

#### Related Code:

Data_collection/simpleAnnotationTool.py

#### Deployment instructions

To run: python simpleAnnotationTool.py Path-to-the-directory-containing-images Path-to-the-parameter-file

The parameter file should look like:

key1 tag1 <br />
key2 tag2 ... <br />

e.g.<br />
1 male<br /> 
2 female<br /> 
3 notSure<br />

* The keys can be simple characters on the key board like 0,1,2,a,b,c, but q can not be used.
* Press key to annotate (map from keys to tags is in the parameter file)
* Press space to skip current image
* The annotation file will be stored in the same directory with the images
* Press q to quit

## Roman Statue Face Pre-process Pipeline and Face Frontalization

Extract the face from the image and frontallize the face(convert any profile view to front view)

#### Deployment instructions


There are 2 modes in /ML4RomeArt/facePrepPipeline

* For face extraction : mode=0

python facePrepPipeline.py  'path_to shape_predictor_68_face_landmarks.dat' 'path_to_dataset'

* For face Frontalization : mode =1

python facePrepPipeline.py  'path_to shape_predictor_68_face_landmarks.dat' 'path_to_face_extracted_dataset'

## Data Augmentation

For better training of the models, it is very important to augment the data. For data augmentation, i have performed rescaling and rotation of image currently. The code for this is /ImageAugmentation.ipynb on /RawImages

## Wrinkle analysis on forehead

Wrinkle analysis on forehead is done on an already annotated dataset present in /forehead_wrinkle_detector/unwrinkled/ and /forehead_wrinkle_detector/wrinkled. I used OpenCV tool Laplacian to:
![alt text](https://github.com/rohit256/Roman-Art-Analysis/blob/master/image.png)

The 2-d array would look like:

[ 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
   0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
   0  0  0  0  0  0  1  3  4  5  7 10 11 12  9 11 14 10 14 16 16 17 19 16
  21 21 17 19 17 14 15 14 11 11  7  5  0  0  0  0  0  0  0  2  0  0  1  0
   1  0  3  0  0  0  3  0  0  0  0  0  3  3  4  6  2  2  2  2]<br />
 [ 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  1  0  1  0  0  0  0
   0  0  0  0  1  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
   0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  1
   0  3  7  6 10 16 20 23 23 20 14 10  6  7  2  3  3  4  0  0  3  4  1  4
   1  4  0  1  0  0  0  0  0  0  0  0  0  0  0  0  1  0  0  0]

Where higher values are for white lines (presence of wrinkle). Now, I have written a very basic algorithm to detect the presence of a line from this 2-d array. Even on applying this basic algorithm, the accuracy of classification was 94% on 100 images tested(50 wrinkled and 50 unwrinkled). A better algorithm can be applied.

#### Deployment instructions

Just run /forehead_wrinkle_detector/Run.ipynb

#### Work reference

Some part of the work done(Data Collection and Annotation) has been taken from 'https://github.com/RedHenLab/RomanArtAnalysis'. This was the work done during 2016 Gsoc for Red hen on Roman Art Analysis. The codes were written in Python 2.7, so i made some changes and minor bug fixes to reproduce the code in python3. Some minor changes were :<br />
 * urllib<br />
 * unicode,str errors<br />
 * inserting into file etc.
<br />
Wrinkled and unwrinkled dataset and wrinkle analysis code has reference from https://github.com/fatchur/Analysis-of-facial-wrinkles

 


