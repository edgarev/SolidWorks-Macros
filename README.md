# SolidWorks-Macros

Personal collection of macros to automate repetitive or missing functionality in SolidWorks. While the code is far from perfect and dosen't always follow best practices, I hope they can be of utility to the community.

All macros have been tested with SolidWorks 2020 SP5.0

Included you may find:
* VBA Macro files for SolidWorks.
* Templates and dependencies for macros.

This macro collection consists of:
## ASSEMBLY MACROS

### Fast BOM Export.swp
* Exports BOM file directly to ".txt".
* ".txt" format is exported significantly faster than exporting to an excel file.
* ".txt" format is preferred over ".csv" for two main reasons:
    * Commas are usable characters in custom properties.
    * Tabulations are discouraged in custom properties.

### Rename virtual components
* When turning the children of an assembly to virtual components they are named by default "Copy^[Assembly Name]".
* Renames all virtual components to exclude the "Copy^..." section of the component's name.

### Add Primitive
* Opens a menu that allows adding a new part template document to the current assembly, while retaining the assembly's properties.
    * For example, the generated part will share the "Project", "Designer", "Priority", ... properties with the parent assembly.
* Configure the part document templates by changing the constant "TemplateFolder" in the "constants" module.
* Assigns a new part number to the filename with the following considerations:
    * File is saved in the same folder as the parent assembly.
    * Requires the last three characters of the parent's file name to be integers.
    * Part number is assigned by getting the next available number following the parent's numeration.
        * PARTS & ASSEMBLIES are assigned unique numbers.

### Duplicate Selected
* Duplicates the file of the selected component and assigns a new part number following the considerations:
    * Requires the last three characters of the parent's file name to be integers.
    * Part number is assigned by getting the next available number following the parent's numeration.
        * PARTS & ASSEMBLIES are assigned unique numbers.

### Save Form New Assembly
* Similar to the inbuilt function "Form New Subassembly" but copies over the properties of the parent assembly to the new subassembly.
* Assigns a new part number following the considerations:
    * Requires the last three characters of the parent's file name to be integers.
    * Part number is assigned by getting the next available number following the parent's numeration.
        * PARTS & ASSEMBLIES are assigned unique numbers.

## BATCH MACROS

### Batch Generation
* Works simlarly to a Design Table, but builds separate files for each parameter set instead of different configurations.
* Is capable of generating parameter sets for both part files and assemblies.
    * Replacing dimensions, replacing components per parameter set, suppressing features and other functions possible with Design Tables.
* Particularily useful for building a custom toolbox or an automated design library.
    * SolidWorks works significantly better with leaner files than those with thousands of configurations (ex. Toolbox fastener parts).

## DRAWINGS MACROS

### Export Each Sheet
* Exports each sheet of a drawing file to a separate ".PNG" file.

### Quick Add Revision
* Simple macro that automates adding a new revision to a revision table, is mostly a time-saver and avoids repetitive clicking.
* Opens a dialog that prompts the user for the revision's information, and enters the insert revision symbol after adding the new row to the revision table.

### Drawing Checklist
* Opens a drawing checklist for self-checking of part and assembly drawings.
* Includes warnings for common mistakes when drafting mirrored parts and other often overlooked properties, like part quantity (not synced to BOM).
* If path is setup, adds a approval design stamp to the file before exporting to PDF, and immediately removes it after exporting.
* Creates the following directories:
    * "DELIVERABLES", same level as parent folder of current file.
    * "DELIVREABLES\CAD 3D", contains folders for parasolid and step file generation.
    * "DELIVREABLES\CAD 2D", contains folders for PDF and DXF file generation.

## Hotkeys

### Show Planes
* Toggles Bounding Box, primary planes and auxiliary planes from view.
* Useful when hiding reference elements before printing a drawing.
* Also useful when designing in a large assembly and hiding reference elemetns from the viewport.
* Commonly assigned to a Hotkey for easier access.

## Parts

### Colors
* Changes the current part's color and assigns a value describing the finish type to the custom property "FINISH".
* Very simple macro, can be edited to include other finishes, or change the final property.
* Is built in multiple files instead of a Userform because it's commonly used as macro buttons in a dedicated custom tab for quicker access.

### Renumber Cut List
* Renumbers all sub-parts in a weldment-based solid with the parent's part number. Changes each weldment body's part numebr to the parent's part number, followed by a "-#" nomenclature.

### Save Cut List Parts
* Saves each weldment body to a separate part file.

### Rename Faces
* Requires selecting multiple faces before executing macro.
* Renames all faces sequentially, in the same order as they were selected.
* Useful for ensuring different solids share references.
    * For example, when building a toolbox, if two screws are built from different base models, none of their faces would have the same internal ID, breaking mates when replacing components between the two part families.
    * By renaming faces in all families in the same sequence, this problem is averted.
    * Similar end result to CATIA's surface publishing feature.

### Save Copy As New Part Number
* Creates and opens a new file derived from the current document.
* Does not replace the old document.
* Similar to "Save As Copy and Open" native functionality.
* Assigns a new part number following the considerations:
    * Requires the last three characters of the parent's file name to be integers.
    * Part number is assigned by getting the next available number following the parent's numeration.
        * PARTS & ASSEMBLIES are assigned unique numbers.

### Save Copy As New Part Number
* Creates and opens a new file derived from the current document.
* Reeplaces the old document.
* Similar to "Save as" native functionality.
* Assigns a new part number following the considerations:
    * Requires the last three characters of the parent's file name to be integers.
    * Part number is assigned by getting the next available number following the parent's numeration.
        * PARTS & ASSEMBLIES are assigned unique numbers.

## Properties

### Add Bounding Box
* Adds bounding box to the current part document.
* Asks the user wether the part is prismatic or turned.
* Assigns the respective value of the bounding box to the following properties:
    * DIAMETER, THICKNESS, WIDTH, LENGTH

Special thanks to countless SolidWorks Forums, Reddit, & Eng-Tips Engineering Forum users whose macro ideas and requests were of great usefulness for my own learning and testing.