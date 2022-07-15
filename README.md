# Challenge Agreed

**Files are in the data folder**

Tools (use any or all of the following):

- Python (preference)
- Qgis
- Google Earth Engine
- others you need/want

## Task 1

Build a plot of the overlapping.csv file and save it in the plot folder.

![image](https://github.com/Agreed-Earth-LTD/challenge/blob/cc2d7232695dce9660b6468f579c8a321ec7f284/img/outwoods.jpg)

Build a plot of the Outwoods_Warren.shp file, save it in the plot folder, code as task1.py and comments in task1.md

**Bonus:** compare using a symmetrical difference method

![image](https://github.com/Agreed-Earth-LTD/challenge/blob/45f7cb9cc981ea71e57d4ac5203d5315ab7f59fc/img/sd.jpg)

save it in the plot folder code as bonus.py and comments in the bonus.md file

## Task 2

Read the predictions.csv file and build a plot of the predictions

![image](https://user-images.githubusercontent.com/13650586/178805195-f75c4ccb-fc5b-4c69-ab3a-e7f73fc1f54d.png)

Compare with the field truth in outwoods.shp file. What can you see? Compare year over year data and determine if the accuracy of the prediction model improves. 
Save the plot as .png, python code as task2.py and your comments in task2.md

## Task 3

What method do you propose to improve a coarse resolution satellite image?
save your comments in the task3.md file

## Task 4 Google Earth Engine (Optional - not directly relevant)

Add a cloud mask to the script and save it as gee.js

```
var geometry =ee.Geometry.Polygon(
        [[[-0.3697612069195966, 50.87460964843314],
          [-0.3697612069195966, 50.85662477701351],
          [-0.3220393441266278, 50.85662477701351],
          [-0.3220393441266278, 50.87460964843314]]], null, false);
function addNDVI(image) {
  return image.addBands(image.normalizedDifference(['B5', 'B4']).rename("ndvi"))
}

var collection = ee.ImageCollection("LANDSAT/LC08/C01/T1_TOA")
      .filterDate('2019-02-01', '2019-09-01')
      .map(addNDVI)

var composite = collection.qualityMosaic('ndvi')

print(ui.Chart.image.series({
  imageCollection: collection.select('ndvi'), 
  region: geometry, 
  reducer: ee.Reducer.mean(),
  scale: 100
}))
```
[GEE Link](https://code.earthengine.google.com/3d3839b3cd9c590b88d3994982c6d8bd)

## Task 5

Make a Pull request with your solution


