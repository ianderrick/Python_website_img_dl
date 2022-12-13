import os
import requests
from bs4 import BeautifulSoup

# Set the URL you want to download images from
url = 'https://www.example.com'

# Set the directory you want to save images to
save_dir = './images'

# Create the save directory if it doesn't exist
if not os.path.exists(save_dir):
    os.makedirs(save_dir)

# Request the HTML page
response = requests.get(url)

# Parse the HTML page
soup = BeautifulSoup(response.text, 'html.parser')

# Find all image tags on the page
img_tags = soup.find_all('img')

# Iterate over the image tags and download the images
for img_tag in img_tags:
    # Get the image URL
    img_url = img_tag['src']

    # Save the image to disk
    try:
        img_data = requests.get(img_url).content
        with open(os.path.join(save_dir, os.path.basename(img_url)), 'wb') as f:
            f.write(img_data)
    except:
        print(f'Error downloading image from URL {img_url}')

print('All images have been downloaded!')
