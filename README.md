# To provide a black t-shirt without any designs or other elements, we will fill the design areas with a solid black color.
import numpy as np

# Convert the image to RGBA mode to manipulate transparency if necessary
img = cropped_img.convert("RGBA")
data = np.array(img)

# Define the black color
black = [0, 0, 0, 255]  # RGBA for black with full opacity

# Set all non-black pixels to black (this will effectively remove the designs)
# We'll apply a threshold to ensure near-black pixels are turned black too
threshold = 100  # Can be adjusted for sensitivity

for row in data:
    for pixel in row:
        # If any RGB value is above the threshold, set the pixel to black
        if any(channel > threshold for channel in pixel[:3]):
            pixel[:3] = black[:3]  # Make it black

# Convert the modified data back into an image
cleaned_img = Image.fromarray(data, mode="RGBA")

# Show the final cleaned image
cleaned_img.show()
