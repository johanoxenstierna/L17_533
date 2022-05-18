## Instances for the Storage Location Assignment Problem (SLAP) on a modified TSPLIB format

### Modifications
- They are currently only stored in JSON format because that is easier to work with than text files.  
- Each warehouse layout comes with a "tsplib_parent" file which gives general required info on the warehouse (see the README in LINK for more details).
- Apart from the addition of the ORDERS tag to the TSPLIB, these instances also come with two new tags: SKUS_TO_SLOT and ASSIGNMENT OPTIONS:
  - SKUS_TO_SLOT: Gives the id of the SKUs that are to be given a new location (slotting). 
  - ASSIGNMENT_OPTIONS. These contain:
    - assignmentType, which for now is only firstAssignment, which means that a set of SKUs previously not in the warehouse are to be placed in the warehouse.
    - evaluationData, which for now is only pickingLog, which means that a picking log is provided with the instance and that the quality of the assignment is to be based on total travel distance of the completed picking log.
    - openLocations, which for now is only allExceptPickingLog, which means that SKUS_TO_SLOT can be placed in any location in the warehouse except for the locations occupied by the SKUs in the picking log.
  
### Solutions
Currently the solutions are expressed in location assignments in instance_name_sol.json. In that json the keys are SKUs and the value is the location (as according to LOCATION_COORD_SECTION in the parent tsplib). 
Solutions for OBP optimization are not included. Although including OBP solutions would be desirable they cannot be required because the OBP model is only used here to provide a distance estimate for the SLAP solution.
The SLAP solution cost hence shows what is achievable (with relative ease) if the corresponding OBP is optimized, but the OBP solution itself is not provided.  
