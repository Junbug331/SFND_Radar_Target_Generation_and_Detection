# SFND Radar Target Generation and Detection

## CFAR Implementation 

### Implementation steps for the 2D CFAR process 
    1. Training Band rows(Tr), Trainig Band columns(Td), Guard Band rows(Gr), Guard Band columns(Gd) and offset are selected for window matrix and threshold offset.
    2. Slide the window matrix over RDM matrix.
    3. At each cell, threshold is calculated by summing all the training cells and averaging it. This calculation is done by first, getting a total sum of window and subtracting the guard portion of the window and finally averaging it.
    4. Add the offset to threshold.
    5. Check if CUT is valid. It's valid if value at CUT is greater or equal than the threshold. If it's valid it's set to 1, otherwise 0.
    6. After sliding the window matrix(when iteration is ended), Set the edge cells in RDM matrix to 0 to get final result matrix.

### Selection of Training, Guard cells and offset. 
    Training Band rows, Training Bamd columns, Guard Band rows and Guard Band columns are defualt suggested values. For the offset, the default value(6) needed to be increased to filter out noise signals. Noise started to disappear when it was set to 8 and onward.

### Steps taken to suppress the non-thresholded cells at the edges 
    non-thresholded cells at the edges are set to 0 by setting each edge side(top, down, left, right) to 0.
    It is done by matlab matrix indexing. (i.e. top edge RDM(1:Tr+Gr,:) = 0)
