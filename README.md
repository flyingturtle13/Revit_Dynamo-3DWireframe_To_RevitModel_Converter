# Revit Dynamo - 3D Wireframe to Revit Model Conversion
This script helps to enhance coordination between architects and structural eningeers during design development.  This script is especially useful for complicated structures and automates converting a 3D wireframe (DWG format) to structural members in Revit during the design coordination iterative process. This can then serve as a foundational model for the structural engineer to update member sizes or add structural members in Revit after structural analysis is performed.

The script requires a DWG file format linked into the Revit model. Using Dynamo Player, user is prompted to selected which linked CAD element to process.  Based on layers in the CAD file, user can specify which model category to apply to a layer. It is important for the structural engineer to communicate to the architect what structural memer layer types and how to assign 3D wireframe elements to which layers in their authoring software (i.e. Rhino). This is especially important when differentiating between structural columns and structural framing elements. This script only applies to modeling structural elements to a 3D wireframe. User still needs to update element parameters such as Structural Usage or Start/End Connections.    

**NOTE:** The Model Examples Folder contains a sample 3D wireframe and output structural Revit model.

## Getting Started
Environment setup regarding script development logistics.

* IDE:
  * Revit Dynamo

* Language:
  * Visual Programming / Python for Custom Node Creation

* Output File Type:
  * dyn

* Additional Library Packages Implemented: </br>
  * Data Shapes
  * BimorphNodes

## Dynamo Script Development & Structure
#### Script features and specs.
* Software Required
  - Revit (any version with Dynamo 2.1 and above installed)
    
* User Interface
  - User executes Dynamo Player to initiate script
  -Data Shapes MultipleInputForm++ node used to obtain user input to perform structural modeling task

#### Dynamo Script Layout
Overall graph view
<p align="center">
  <img src="https://user-images.githubusercontent.com/44215479/81253410-5c75f480-8fdd-11ea-9512-8514686a6725.png" width="600">
</p>

1. User Input
<p align="center">
  <img src="https://user-images.githubusercontent.com/44215479/81253905-85e35000-8fde-11ea-8d98-efc1499fd302.png" width="400">
</p>

2. Example of Backend Process for a parameter
    * **Note:** A warning may be indicated as an elements(s) may not have the parameter applicable to it.  See Output (Watch node) which element has a null value.  This can be ignored. 
<p align="center">
  <img src="https://user-images.githubusercontent.com/44215479/81253998-c93dbe80-8fde-11ea-99f7-df813fc4c3af.png" width="600">
</p>

3. Mapping Script to UI
<p align="center">
  <img src="https://user-images.githubusercontent.com/44215479/81255262-1707f600-8fe2-11ea-847a-2806dda91c97.png" width="600">
</p>
       
## Running Script & User Implementation Instructions
1. Clone or download project. </br>
2. In own Revit project or using example Revit model in Example Revit Model folder, load shared parameters from Revit_DynamicParameter_Export.txt
<p align="center">
  <img src="https://user-images.githubusercontent.com/44215479/81255753-5be05c80-8fe3-11ea-897c-1e05fd6803f1.png" width="400">
</p>
3. Select an model element (e.g. wall, floor, etc.), to confirm shared parameters are loaded.
<p align="center">
  <img src="https://user-images.githubusercontent.com/44215479/81255898-c1344d80-8fe3-11ea-8dfd-5aa9977640ee.png" width="600">
</p>
4. Open the Dynamo script (RevitMetaDataExporter.dyn) in Dynamo. </br>
5. In the User Input section (Select Model Elements node), select and drag select all the desired elements to be processed in the Revit 3D view and select Run in Dynamo.
   <p align = "center">
      <img src="https://user-images.githubusercontent.com/44215479/81256281-db226000-8fe4-11ea-8c00-5fb1068cd275.png" width="600">
   </p>
6. In a Revit 3D view, select an element and check that shared parameters have been updated
   <p align = "center">
      <img src="https://user-images.githubusercontent.com/44215479/81256570-c09cb680-8fe5-11ea-8a4d-5c5e7e185723.png" width="400">
   </p>

## References for Further Learning
- [Using Datasmith with Revit - Epic Games Unreal Engine](https://docs.unrealengine.com/en-US/Engine/Content/Importing/Datasmith/SoftwareInteropGuides/Revit/index.html)
- [Using Datasmith Metada - Epic Games Unreal Engine](https://docs.unrealengine.com/en-US/Engine/Content/Importing/Datasmith/Overview/UsingDatasmithMetadata/index.html)


