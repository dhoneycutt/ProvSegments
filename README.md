Brett's Provenance Visualization Tool
===================================

Preprocessing
------------------------------------
All relevent files are in the "code" folder.

The python script "provenance.py" conducts preprocessing on the "Segmentation" and "User Interaction" folders in each "code\ProvSegments\Dataset_X" folder. 
It converts segment csv files into json and merges all user interaction json into a single file for use with d3.

The python script requires an argument to run and its output piped to a json file. The argument specifies whether a merging proceedure is to be conducted to reduce the number of segments. The merging proceedure naively merges segments >1/24th the total time with an adjacent neighbor segment.

To NOT merge (recomemended):
```
python provenance.py 0 > vis.json
```

To merge:
```
python provenance.py 1 > vis.json
```

Adding New Segments
--------------------------------

To add new files:

**1)** New segment files must have the following format and the same file names as the orginal segments in "Dataset_X/Segmentation":
```
ID  start end length (sec)
0 0 112.7 112.7
1 112.7 438.9 326.2
2 438.9 586.1 147.2
3 586.1 590.8 4.7
4 590.8 636.6 45.8
...
```

**2)** Copy the old segments in the "Segmentation" folder somewhere for safekeeping.

**3)** Replace segments in the "Segmentation" folder with new files made in **1)**.

**3)** Run provenance.py again.

Running the Visualization
---------------------

**1)** Run localserver.bat.

**2)** Go to [http://localhost:8080/index.html](http://localhost:8080/index.html).
