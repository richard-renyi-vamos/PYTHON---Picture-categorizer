ChatGPT conversation

*********

ChatGPT
Picture Categorizer

Answer in chat instead
Here is a Python script for a picture categorizer. It organizes images into folders based on their dimensions (width x height). 📸✨

Let me know if you need any enhancements or further assistance! 🚀😊

import os
import shutil
from PIL import Image

def categorize_pictures(source_dir, output_dir):
    """
    Categorize pictures into folders based on their dimensions.

    Args:
        source_dir (str): Path to the source directory containing pictures.
        output_dir (str): Path to the output directory where categorized folders will be created.
    """
    if not os.path.exists(output_dir):
        os.makedirs(output_dir)

    for file_name in os.listdir(source_dir):
        file_path = os.path.join(source_dir, file_name)
        
        if not os.path.isfile(file_path):
            continue

        try:
            with Image.open(file_path) as img:
                width, height = img.size
                category = f"{width}x{height}"

                category_dir = os.path.join(output_dir, category)
                if not os.path.exists(category_dir):
                    os.makedirs(category_dir)

                shutil.copy(file_path, category_dir)

        except Exception as e:
            print(f"Error processing {file_name}: {e}")

if __name__ == "__main__":
    source_directory = input("Enter the source directory path: ")
    output_directory = input("Enter the output directory path: ")

    categorize_pictures(source_directory, output_directory)
    print("Picture categorization completed successfully! 😊")
