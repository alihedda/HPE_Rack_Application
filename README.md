# 1- Installation

We should install the environments and packages management system:
* Anaconda fro Windows: https://www.anaconda.com/
* Miniconda for linux: https://docs.conda.io/en/latest/miniconda.html

Then using the configuration file YAML **'./environment.yml'** create the environment throw the terminal or an Anaconda Prompt:

```shell  
> conda env create -f environment.yml
```

Then activate the environment

```shell  
> conda activate keras-cpu
```

# 2- Try the python prediction function

Go to the folder 
```shell  
> cd HPE_Rack_server_components
```

Put any image of the HPE Rack server under the folder **"./image/in"** with the name **"img.jpg"** then execute the test script:

```shell  
> python test.py
```
Rq: It may happen some problems where the model h5 file don't be successfully downloaded. In this case, we can manually downloded from https://drive.google.com/file/d/11Y8T46zceapWiBd1o4_kOjA6AVgGWJ1u.

As a result we get a list of lists (objects). Each one has this format [xmin, ymin, xmax, ymax, class_index, confidence].
(xmin, ymin) and (xmax, ymax) are the coordinate of the two points that define the bounding box.
class_index is from 0 to 10 corresponding to the class name into the file **"./model/classes.txt"**.
Another result is the image with the bounding boxes drawn on it. This image is saved to **"./image/out/img.jpg"**.

# 3- API

to launch the api execute this shell in one terminal

```shell  
> python app.py
```

and to test the web service, we should open a new terminal and use the next python script
```shell  
> python request.py
```
# 4- Result example
```json
{
  'numObjects': 8,
  'threshold': 0.25,
  'objects': [
    {
      'name': 'object',
      'className': 'HP_StorageWorks_Ultrium_960',
      'score': 0.7603004,
      'x': 415,
      'y': 139,
      'height': 539,
      'width': 167
    },
    {
      'name': 'object',
      'className': 'HP_StorageWorks_MSA2000',
      'score': 0.89178616,
      'x': 423,
      'y': 401,
      'height': 515,
      'width': 115
    },
    {
      'name': 'object',
      'className': 'HP_ProLiant_DL785_G6',
      'score': 0.56284434,
      'x': 443,
      'y': 1606,
      'height': 453,
      'width': 301
    },
    {
      'name': 'object',
      'className': 'HP_ProLiant_DL385_G6',
      'score': 0.9228288,
      'x': 412,
      'y': 786,
      'height': 531,
      'width': 117
    },
    {
      'name': 'object',
      'className': 'HP_ProLiant_DL385_G5p',
      'score': 0.93396425,
      'x': 437,
      'y': 1297,
      'height': 470,
      'width': 113
    },
    {
      'name': 'object',
      'className': 'HP_ProLiant_DL380_G6',
      'score': 0.78895193,
      'x': 414,
      'y': 306,
      'height': 534,
      'width': 104
    },
    {
      'name': 'object',
      'className': 'HP_ProLiant_DL380_G5',
      'score': 0.7489091,
      'x': 413,
      'y': 631,
      'height': 536,
      'width': 110
    },
    {
      'name': 'object',
      'className': 'HP_ProLiant_DL360_G7',
      'score': 0.59229493,
      'x': 383,
      'y': 1016,
      'height': 592,
      'width': 60
    }
  ]
}
```
