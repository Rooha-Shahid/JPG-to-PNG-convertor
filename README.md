# JPG-to-PNG-convertor
import sys
import os
from pathlib import Path
from PIL import Image, ImageFilter
     
# defining arguments
p1 = str(sys.argv[1])  
p2 = str(sys.argv[2])

# making directory
if not os.path.exists(p2):
    os.mkdir(p2)

# giving path to iterate, better to use os.listdir() option as it keeps the same filename
entries = Path(p1)      

# iterating over files
i = 1
for entry in entries.iterdir():         
    jpg_img = Image.open(entry)
    if os.path.exists(p2 + 'pic.png'):
        png_img = jpg_img.save(p2 + 'pic' + str(i) + '.png', 'png')
    elif os.path.exists('pic' + str(i) + '.png'):
        png_img = jpg_img.save(p2 + 'pic' + str(i+1) + '.png', 'png')
    else:
        png_img = jpg_img.save(p2 + 'pic.png', 'png')


    i += 1



# use this command in terminal before running code file bto remove .DS_Store files so all files are JPEG in the folder
# find . -name "*.DS_Store" -type f -delete




