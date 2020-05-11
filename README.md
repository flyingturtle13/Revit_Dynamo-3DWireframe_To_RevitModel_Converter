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
   <img src="https://user-images.githubusercontent.com/44215479/81614036-4cbb2f00-9394-11ea-9b2a-2e84bdc03692.png" width="1000">
  </p>

1. User Input
   * Uses Data Shapes package to create input types and to be used in MultipleInputForm++ (obtain user input)
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81614113-68bed080-9394-11ea-9d35-36fa42638d04.png" width="600">
   </p>

2. Example of Backend Process Per User Input
   * This process makes the selected linked CAD file easily accessed for processing by removing nested lists
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81614285-ac193f00-9394-11ea-80ee-41c54d201a2e.png" width="600">
   </p>

3. User Input
   * Uses Data Shapes package to create input types and to be used in MultipleInputForm++ (obtain user input)
   * Creates consolidated list taking user selection from (2.) and model family type information from (1.).
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81615475-82f9ae00-9396-11ea-8b5c-f72cbfe847e6.png" width="600">
   </p>

4. Example of Backend Process Per User Input
   * Each process accesses user input by associated list index
     * The selected layer will be used to access 3D lines on that layer to be converted to curves (using BimmorphNodes - CAD.CurvesFromCADLayers node)
     * The selected structural frame or structural column type is assigned to curve if user has checked the box for type to be modeled
     * The selected level is assigned for element level association.
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81615475-82f9ae00-9396-11ea-8b5c-f72cbfe847e6.png" width="600">
   </p>

5. Revit Model Element Created
   * StructuralFraming.BeamByCurve or StructuralFraming.ColumnByCurve Node is used to take the user input from (4.) to generate a Revit model element.
   * This is repeated for all curves filtered by user selected CAD Layer.
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81616796-03b9a980-9399-11ea-9cee-2acacfb1cf87.png" width="600">
   </p>
   
#### Mapping Script to UI
1. UI associated to (Dynamo Script Layout 2.)
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81255262-1707f600-8fe2-11ea-847a-2806dda91c97.png" width="600">
   </p>

2. UI associated to (3.) resulting from user input from (Dynamo Script Layout 2.) and information from (Dynamo Script Layout 1.).
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81617573-8b53e800-939a-11ea-9cbd-500da098e4f4.png" width="200">
   </p>

3. Resulting Output after applying Revit structural elments to column layer and brace layer associated to (Dynamo Script Layout 5.).
   <p align="center">
    <img src="https://user-images.githubusercontent.com/44215479/81617857-0cab7a80-939b-11ea-8f89-c6af9464e659.png" width="600">
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


