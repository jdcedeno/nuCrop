# nuCrop
Project developed for Entopsis, LLC

This project was requested by Entopsis, LLC. They needed a program that could detect the 'Nutec' slides contained in each image, then automatically crop and save each slide as another individual image file. The original images could contain from 1 to 6 slides and could be randomly placed in a 3-by-2 grid.

The images looked something like this:

![input image](https://raw.githubusercontent.com/jdcedeno/nuCrop/master/images/1.%206%20NuTecs%2C%20vertical%2C%20bigger%20area.jpg)

I had recently taken a Computer Vision course at Florida International University, which led me to the idea of using the mean of sections of the images to detect the position of each slide. There were some conditions that I noticed:

* The input image size in pixels is always similar (not the same but close) and the difference is negligible
* The background is always black
* Slides are always bright (close to white)
* The places that did not contain slides were white
* Slides are always placed in a 3-by-2 array
* Slides have a similar size in pixels among all the input images

I decided to use this data to find the location of the slides in the image. I scanned the mean of 'bands' that spanned the whole width/height of the image and 'slid' it vertically/horizontally to determine the top, bottom, left, and right edges where the slides were located. This produced a new image that had the black background cropped out.

After that, I found the threshold mean value to decide whether an image contained a slide or not. Knowing that the slides had a similar distribution and pixel size along all the input images, I could determine a fixed pixel value for the width and height of the slides along all input images.

For the GUI design, I used a Python library called TKinter. This was the first time I developed anything like that so I only has the basic buttons for functionality.

![main window](https://github.com/jdcedeno/nuCrop/blob/master/images/nuCrop%20main.JPG)

In order to guide the program user, the only active button when the app initializes is the 'Browse' button.

![browse window](https://raw.githubusercontent.com/jdcedeno/nuCrop/master/images/nuCrop%20browse.JPG)

After you select an image file, you can either browse again to select another image file or click the 'Crop' button which will run the detection algorithm. After this, the 'Validate' and 'Save' buttons are enabled.

![validate window](https://raw.githubusercontent.com/jdcedeno/nuCrop/master/images/nuCrop%20validate.JPG)

Finally, the resulting images are automatically saved under the file path: original-name_chamberN.jpg

![validate window](https://raw.githubusercontent.com/jdcedeno/nuCrop/master/images/nuCrop%20result.JPG)


