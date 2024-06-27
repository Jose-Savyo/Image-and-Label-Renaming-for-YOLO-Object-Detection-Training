# Image and Label Renaming for YOLO Object Detection Training

This repository contains a Python notebook designed to automate the renaming of image files and their corresponding label files. This process is crucial for preparing datasets for training YOLO (You Only Look Once) models for object detection.

## Description

The provided notebook iterates through a specified directory of image files and their corresponding label files. It renames each file in a sequential order (e.g., `O_1.jpg`, `O_1.txt`, `O_2.jpg`, `O_2.txt`, etc.), ensuring that the images and their labels maintain a consistent naming convention required for training YOLO models.

## Notebook Overview

The main steps performed by the notebook include:

1. **Listing Image Names**: Lists all image names from the specified directory.
2. **Creating New Names**: Generates a list of new names for the images and labels.
3. **Renaming Files**: Renames the image and label files according to the new naming convention.

## Usage

### Prerequisites

- Python 3.x
- Jupyter Notebook
- Necessary directories containing your image and label files

### Steps to Use

1. Clone the repository to your local machine:

    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    cd your-repository-name
    ```

2. Open the notebook `RENAME_for_images_and_labels.ipynb` in Jupyter Notebook or Jupyter Lab.

3. Set the paths to your image and label directories in the notebook:

    ```python
    folder_images = 'path/to/your/images'
    folder_labels = 'path/to/your/labels'
    ```

4. Run the notebook cells to perform the renaming operation.

## Code Example

Here's a brief snippet of the code used in the notebook:

```python
import os

# Define the paths to the image and label directories
folder_images = 'test/images'
folder_labels = 'test/labels'

# List files in the directories
images = os.listdir(folder_images)
labels = os.listdir(folder_labels)

# Iterate through images and rename them along with their corresponding labels
for index, image in enumerate(images):
    new_name_image = f'O_{index + 1}.jpg'
    new_name_label = f'O_{index + 1}.txt'
    
    old_path_image = os.path.join(folder_images, image)
    new_path_image = os.path.join(folder_images, new_name_image)
    
    old_path_label = os.path.join(folder_labels, image.strip('.jpg') + '.txt')
    new_path_label = os.path.join(folder_labels, new_name_label)
    
    # Rename the image
    os.rename(old_path_image, new_path_image)
    print(f'Renamed {image} to {new_name_image}')
    
    # Rename the label
    os.rename(old_path_label, new_path_label)
    print(f'Renamed {image.strip('.jpg') + '.txt'} to {new_name_label}')
