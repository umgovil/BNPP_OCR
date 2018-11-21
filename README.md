# BNPP_OCR

<h1>Optical Character recognition using PyTesseract</h1>

An English word image generators, to recognize the word from the image.

First, imports are handled. The Image class is used to load our input image from disk in PIL format, a requirement when using pytesseract .

Then, the two command line arguments are parsed:
<ul>
  <li>--image : The path to the image we’re sending through the OCR system.
  <li>--preprocess : The preprocessing method. This switch is optional and for this tutorial and can accept two values:  thresh  (threshold) or blur .
</ul>

Next the image is loaded, binarized, and written to the disk throught the following steps:
<ol>
  <li><strong>Lines 17, 18:</strong> Loading image to memory followed by converting it to grayscale
  <li><strong>Lines 22-24:</strong> Performing a threshold to segment the foreground and background. This is done using  cv2.THRESH_BINARY  and cv2.THRESH_OTSU  flags.
  <li><strong>Lines 28-29:</strong> Performing a median blur when the --preprocess  flag == blur . Applying a median blur helps reduce noise making it easier for Tesseract to identify the characters in the image.
  <li><strong>Line 33:</strong> os.getpid is used to derive a temporary image filename based on the process ID of our Python script.
  <li><strong>Line 34:</strong> Write the pre-processed image to the disk saving it with the above mentioned filename.
  <li><strong>Lines 38-40:</strong> pytesseract.image_to_string is used to convert the contents of the image into our desired string "text" . A reference is passed to the temporary image file residing on disk, which is followed by some cleanup where the temporary file is deleted. The ouput string "text" is printed  to the terminal.
</ol>

The code is executed by inputting the following command in the terminal: python ocr.py --image example_03.png

Code referenced from tutorial website: https://www.pyimagesearch.com/2017/07/10/using-tesseract-ocr-python/
