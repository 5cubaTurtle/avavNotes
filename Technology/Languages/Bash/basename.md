#bash #path 
strip directory and suffix from filenames

strip the path from filepath:  `basename src/autonomy/behaviors/explore_floor_behavior.py`, this outputs:   `explore_floor_behavior.py`
- `-a`   support multiple arguments

strip the file from filepath:   `dirname src/autonomy/behaviors/explore_floor_behavior.py`, this outputs:   `src/autonomy/behaviors`