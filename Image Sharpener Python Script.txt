from PIL import Image, ImageEnhance, ImageFilter
import os

path = './Base Images'
pathOut = '/Edited Images'

for filename in os.listdir(path):
    img = Image.open(f"{path}/{filename}")

    edit = img.filter(ImageFilter.SHARPEN)

    enhancer = ImageEnhance.Contrast(edit)
    edit = enhancer.enhance(1.5)

    clean_name = os.path.splitext(filename) [0]

    edit.save(f'.{pathOut}/{clean_name}_edited.jpg')

imageObject = Image.open(f'.{pathOut}/{clean_name}_edited.jpg')
imageObject.show()