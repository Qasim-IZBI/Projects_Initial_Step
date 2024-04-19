# Projects_Initial_Step

### Create directory based on file name and move file to the directory (in conda prompt):
`for %I in (*.czi) do (mkdir "%~nI" && move "%I" "%~nI")`

### Create list of the location of the images (in conda prompt):
`dir /b /s *.czi > image_paths.txt`

### Import image_paths in qupath
