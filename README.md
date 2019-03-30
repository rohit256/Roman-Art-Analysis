# Roman Art Analysis

The work done focuses on analysis of the images of ancient roman statues for their social values.
This project contains parts as follow:

1. webpage parsers for data collecting from art databases

2. simple annotation tool for roman statue images

3. roman statue face extraction

4. face frontalization

5. Wrinkle analysis on forehead using Soft computing and algorithms


## Webpage Parsers for data Collectiion from Art Databases

The HTMLParser and state machine is used for parsing the webpages of the databases and downloading images and meta-data.

#### Related Code:

-> Data_collection/downloader4MCLcamacuk.py: parsing the webpage 'http://museum.classics.cam.ac.uk/collections/casts' and download the images.
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

key1 tag1 
key2 tag2 ...

e.g.

1 male 
2 female 
3 notSure

The keys can be simple characters on the key board like 0,1,2,a,b,c, but q can not be used.

Press key to annotate (map from keys to tags is in the parameter file)

press space to skip current image

The annotation file will be stored in the same directory with the images

Press q to quit

## Roman Statue Face Pre-process Pipeline and Face Frontalization

Extract the face from the image and frontallize the face(convert any profile view to front view)

#### Deployment instructions


There are 2 modes in /ML4RomeArt/facePrepPipeline

For face extraction : mode=0

python facePrepPipeline.py  'path_to shape_predictor_68_face_landmarks.dat' 'path_to_dataset'

For face Frontalization : mode =1

python facePrepPipeline.py  'path_to shape_predictor_68_face_landmarks.dat' 'path_to_face_extracted_dataset'


![alt text](https://github.com/rohit256/Roman-Art-Analysis/blob/master/image.png)

#### Work reference

Some part of the work done(Data Collection and Annotation) has been taken from 'https://github.com/RedHenLab/RomanArtAnalysis'. This was the work done during 2016 Gsoc for Red hen on Roman Art Analysis. The codes were written in Python 2.7, so i made some changes and minor bug fixes to reproduce the code in python3. Some minor changes were :
 urllib
 unicode,str errors
 inserting into file etc.

 


