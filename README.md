# Lab 3: Image Compression Using Singular Value Decomposition (SVD)

---

**To get credit for the lab, please show the completed work to a lab instructor.**

## Goals

1. Understand the concept of SVD and its application to image processing.
2. Implement an interactive web application that allows users to compress an image using SVD and adjust the number of singular values retained (rank).
3. Explore the effect of SVD rank on the compressed image.

## Instructions

### Part 0: Setup Environment

Similar to Lab 2, you can use the `Makefile` to install all dependencies. In your terminal, simply run:

```bash
make install
```

This will automatically install the necessary packages listed in `requirements.txt`, including:

- Flask
- Numpy
- Scikit-learn
- Pillow

### Part 1: Implementing SVD for Image Compression

An image is represented as a matrix where each element corresponds to the intensity of a pixel. In the case of an RGB image, there are three such matrices, one for each color channel (Red, Green, Blue).

The core idea of using SVD for image compression is that we can decompose the image matrix into three other matrices, and by retaining only the most important singular values (those that contribute the most to the image's structure), we can compress the image by reducing its data without significantly affecting its appearance.

Your task is to complete the following functions in the provided script:

    - (TODO) `load_image(image_path)`: This function should load the image from a file and return it as a NumPy array. You will need to use the `Pillow` library for this task. You can reuse the code from Lab 2.
    - `image_compression_svd(image_np, rank)`: This function compresses an image by applying SVD separately to each color channel. It has been inplemented for you and will call `compress_channel_svd(channel_matrix, rank)` for single channel processing. 
    - (TODO) `compress_channel_svd(channel_matrix, rank)`: This function applies SVD to compress a single image channel. It should return a compressed single channel image. (You may use NumPy functions for SVD computation.)
    - `save_result(original_image_np, quantized_image_np, output_path)` This function has been provided for you. Once the original and compressed images are prepared, the function will save them side by side in a single image file.

### Part 2: Testing Your Code with a Static Input

1. You can test the code locally by running the Python script directly and specifying an image path. Modify `__main__` in `image_compression_impl.py` to load the image, apply compression, and save the results. Make sure you provide paths for both input and output images.
2. Choose your favorite image as input and experiment with different values of `rank` and observe the effect on image quality. We also have a sample image 'examples/example.jpg' for you to use.

**Example Workflow**

1. Select your favorite image file (e.g., `'favorite_image.png'`) and place it in your working directory.
2. In `__main__`:
    - Set `image_path` to your selected image file.
    - Set `output_path` to where you want to save the side-by-side result (e.g., `'compressed_image.png'`).
    - Choose an appropriate number of sigular values retained (`rank`), e.g., 8.
3. Run the script in your terminal:
   
   python image_compression_impl.py

4. Check the output image to see the original and compressed versions side by side.

### Part 3: Running the Interactive Module

Once the environment is set up, you can start the Flask application by running:

```bash
make run
```

This will start the Flask server and make the interactive application available locally at `http://127.0.0.1:3000`.

The interactive module allows you to upload an image and select the SVD rank for compression through a web interface.

1. Open your browser and go to `http://127.0.0.1:3000`.
2. Upload your favorite image using the provided interface.
3. Enter SVD rank for compression.
4. Click the "Submit" button to perform the image compression.
5. The original and compressed images will be displayed side by side on the page.

### Notes:

1. Ensure that the image loaded is in RGB format.
2. Test with your favorite image and experiment with different values for `rank` to observe the impact of compression.
3. If you encounter issues loading or saving images, check the installation of `Pillow` and the file format compatibility.
4. If you encounter issues running the Flask server, ensure that `flask` is correctly installed and check the command line output for error messages.
