# Projects_Initial_Step

### Create directory based on file name and move file to the directory (in conda prompt):
`for %I in (*.czi) do (mkdir "%~nI" && move "%I" "%~nI")`

### Create list of the location of the images (in conda prompt):
`dir /b /s *.czi > image_paths.txt`

### Import image_paths in qupath


### Create CSV file

```python
import os
import pandas as pd

# Define the directory containing the image files
directory = r'D:\IZBI\Adrian\Ghallab\MECA-32'

# Function to extract information from the filename
def extract_info(file_directory):
    filename = file_directory.split('\\')[-1]
    parts = filename.split(' ')
    week = parts[1]
    condition = parts[2]
    replicate = parts[3].split('.')[0]  # Remove the file extension
    return filename, week, condition, replicate

# List to store extracted information
data = []

# Open the text file for reading
with open(directory + '\image_paths.txt', 'r') as file:
    # Read each line one by one
    for file_directory in file:
        name, week, condition, replicate = extract_info(file_directory)
        data.append([name, week, condition, replicate])

# Create a DataFrame from the data
df = pd.DataFrame(data, columns=['Filename', 'Timestamp', 'Treatment', 'Sample'])

# Save the DataFrame to a CSV file
csv_file = os.path.join(directory, 'image_info.csv')
df.to_csv(csv_file, index=False)

print(f'CSV file "{csv_file}" created successfully.')
```
