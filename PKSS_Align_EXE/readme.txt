Instruction

Used point cloud should be stored as "ply" file.

There have two methods to use the program of PKSS-Align：

1. Use PKSS-Align with default parameter input
    
    Parameter 1: input source file path (Instance：C:\Data\source.ply)
    Parameter 2: input template file path (Instance：C:\Data\template.ply)

    The output point cloud is stored in the path of source file (D:\Data\source_align.ply)


2. Use PKSS-Align with feasible parameter input
    
    Parameter 1: input source file path (Instance：C:\Data\source.ply)
    Parameter 2: input template file path (Instance：C:\Data\template.ply)
    Parameter 3: rotation set (default = 12) 
    Parameter 4: center set (default = 3) 
    Parameter 5: simplification (default = 3000) 
    Parameter 6: initial pose(default = 1) 

    The output point cloud is stored in the path of source file (D:\Data\source_align.ply)

    Note: The rotation set and center set should not be changed with large values (rotation: 10 - 14; center: 1 - 5)
              If the point cloud has obviously defective parts, the center set can be changed to be larger value. On the contray, the center set can be set to 1.
              If the point cloud has obviously geometric structure and raw non-uniform density, initial pose is recommneded to be 1 (Use PCA to align point clouds as the initial processing)