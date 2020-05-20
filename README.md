 # SpatialQuestions
## A Dataset For Context-aware Question Answering 

### Links
:earth_africa: [Webpage](https://spatialquestions.sda.tech/) | :page_facing_up: [Paper](paper/) 

### Introduction
We release a Question Answering dataset containing +5000 questions specifically taking spatial context information into account, i.e. visual features of a surrounding target object, or the user's location and moving direction -- _SpatialQuestions_. The data was collected in a big-scale user study with Amazon's Mechanical Turk platform involving over 400 crowdworkers and annotated semi-automatically in the post-processing. Please refer to our [paper]() for more details about the creation process and dataset statistics. 


### Repository Structure
- `code/`
	+ `mturk.html`: The HTML file that was used as the MTurk form in the experiments
- `resources/`
	+ `RawQuestions.txt`: Raw user input on MTurk without any meta information
  + `SpatialQuestions.json`: Full dataset in JSON format (see below for more details)
  + `HanoverPOIs.ods`: List of all initial anker positions used for the StreetView Embedding in the MTurk survey 
- `LICENSE`: License information
- `README.md`


### Dataset

**License**: You can download the [dataset](resources/SpatialQuestions.json) (released with a [MIT License](LICENSE)), or read below to know more.

**Format**: The dataset is released in JSON format, where the key `Question` contains the question, `ContextInformation` contains the corresponding visual and spatial signals as phrase and/or just the key word, and `PointOfView` contains the meta data extracted from the [StreetView API](https://developers.google.com/maps/documentation/streetview/intro). The dataset has the following JSON structure:

```json
{
    "QuestionId": "Unique question ID as integer",
    "Question": "Question phrased by the crowdworker",
    "StreetView": "Link to the StreetView image showing the focus when the question was phrased",    
    "ContextInformation": {         
        "VisualSignals": "The phrase that contains the visual signals, e.g. 'yellow building'",        
        "Size/Shape/Color/Salience": "Explicit mentions of visible features of the target object, e.g. 'tall tower'",
        "SpatialSignals": "The phrase that contains the spatial signals, e.g. 'behind the fence'",
        "Deixis/Direction/Position/Vicinity": "Explicit mentions of spatial hints to locate the target object in relation to the user, e.g. 'this building' or 'the building to my left'"
    },        
    "PointOfView": {
        "Heading": "0..359",
        "Long": "-180.0..180.0",
        "Lat": "0.0..180.0"
    },
    "DateAndTime": "2019-06-27T11:37:14.000000455", 
    "Properties": "Possible KG properties that the questions targets, e.g. name/label, opening hours, popularity or abstract. Properties are derived from OpenStreetMap."
}
```

### Examples
<details>
  <summary>5 nitpicked examples</summary>

```json  
[
  {
    "QuestionId": 0,
    "Question": "What is the name of that large building behind the fence?",
    "StreetView": "https://www.google.com/maps/@?api=1&map_action=pano&viewpoint=52.375842,9.7404004&heading=355.0&pitch=-1.8020866768683987&fov=120",
    "ContextInformation": {
        "VisualSignals": "large building",
        "Size": "large",
        "Direction": "behind",
        "SpatialSignals": "behind the fence"
    },    
    "PointOfView": {
        "Heading": 355,
        "Long": 9.7404004,
        "Lat": 52.375842
    },
    "DateAndTime": "2019-06-27T11:37:14.000000455",
    "Properties": "name"
  },
  {
    "QuestionId": 1,
    "Question": "Do you know what the plaque on that piece of art in the median says?",
    "StreetView": "https://www.google.com/maps/@?api=1&map_action=pano&pano=ae5tuNJ_xl1TS4dneHSdgA&heading=210.1266758416503&pitch=-19.78025402272617&fov=120",
    "ContextInformation": {
        "VisualSignals": "on that piece of art",
        "SpatialSignals": "in the median"
    },
    "PointOfView": {
        "Heading": 210.1266758,
        "Long": 9.7347076,
        "Lat": 52.3689436
    },
    "DateAndTime": "2019-06-27T12:15:05.000000630",
    "Properties": "inscription"
  },
  {
    "QuestionId": 2,
    "Question": "Are there cafes on this street?",
    "StreetView": "https://www.google.com/maps/@?api=1&map_action=pano&pano=5Kn-R_pqCVXEfbr6g78VYw&heading=56.257219084221944&pitch=0.3299029016246635&fov=120",
    "ContextInformation": {
        "SpatialSignals": "on this street"
    },  
    "PointOfView": {
        "Heading": 56.25721908,
        "Long": 9.738762,
        "Lat": 52.3692021
    },
    "DateAndTime": "2019-06-27T15:10:49.000000988"    
  },
  {
    "QuestionId": 3,
    "Question": "Are there more businesses or houses in this area?",
    "StreetView": "https://www.google.com/maps/@?api=1&map_action=pano&pano=_K8GeBrB21c9wVXBAdJuKg&heading=2.362851134167954&pitch=-8.960466980952447&fov=120",
    "ContextInformation": {
        "SpatialSignals": "in this area"
    },
    "PointOfView": {
        "Heading": 2.362851134,
        "Long": 9.7455448,
        "Lat": 52.3723053
    },
    "DateAndTime": "2019-06-27T14:23:51.000000262" 
  },
  {
    "QuestionId": 4,
    "Question": "Is the jeweler store on the right famous?",
    "StreetView": "https://www.google.com/maps/@?api=1&map_action=pano&pano=xSFL8_WXPspXHmAcs1yI5g&heading=3.603047068367749&pitch=-4.744553947315012&fov=120",
    "ContextInformation": {
        "Direction": "right",
        "SpatialSignals": "on the right"
    },
    "PointOfView": {
        "Heading": 3.603047068,
        "Long": 9.7417629,
        "Lat": 52.3737913
    },
    "DateAndTime": "2019-06-27T17:44:33.000000075",
    "Properties": "famous"
  }
]
```
</details>

### Contact
In case you find any issue with our dataset, please inform us on Issues Page.
Contact jewgeni.rose@volkswagen.de for anything regarding the dataset. 

### Changelog

#### 0.1.0 - 19-03-2020
- First version released

