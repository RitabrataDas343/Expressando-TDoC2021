# What is Computer Vision?

Computer vision is an interdisciplinary field that deals with how computers can be made to gain high level understanding from digital images or videos so the idea is to automate tasks that the human visual systems can do so a computer should be able to recognize that this is a face of a human being, this is what a lamppost looks like so things like that right so i hope i'm clear what is meaning of computer vision.

Computer Vision is a field of study which enables computers replicate the human visual system. As already mentioned above, it's a subset of artificial intelligence which coolects information form digital images or videos and processes them to define the attributes. The entire process involves image acquiring, screening, analysing, identifiying and extracting information. This extensive processign helps computers to usnderstand any visual content and act on it accordingly.

Computer vision projects translate digital visual content inot explicit descriptons to gather multi-dimensional data. This data is then turned into a computer-readable language to aid the decision-making process. The main objective of this branch of artificial intelligence is to teach machines to collect information from pixels.

# How does a computer read an image?

How does a human mind apprehend an image? When you see the image below whtat do you actually see and how do you say what is in the image?

you most probably look for different shapes and colours in the image and that might help you decide that this is an image of a dog. But does a computer also see it in the same way? The answer is no.

A digital image is an image composed of picture elements, alsso knows as pixels, each wiht finite, discrete quantities of numeric representation for its intensity or grey level. So the computer sees an images as numerical values of these pixels and in order to recognise a certain image, it has to recognise the patterns and regularities in this numerical data.

Here is a hypothetical example of how pixels form an image. The darker pixels are represented by a number closer to the zero and lighter pixels are represented by numbers approaching one. All other colours are represented by the numbers between 0 and 1. 

But usually, you will find that for any colour image, there are 3 primary channels – Red, green and blue and the value of each channel varies from 0-255. In more simpler terms we can say that a digital image is actually formed by the combination of three basic colour channels  Red, green, and blue whereas for a grayscale image we have only one channel whose values also vary from 0-255.

# Waht is OpenCV?

OpenCv (Open Soucre Computer Vision Library) is an open source software library for computer vision and machine learning. OpenCV was created to provide a shared infrastucture for applications for computer vision add to speed up the use of machine perception in consumer products. OpenCV, as a BSD-licensed software, makes it simple for companies to use and chagne the code. There are some predefined packages and libraries that makes our life simple and OpenCV is one of them.


# Install OpenCV

## For Windows Or Linux 

you can use pip to install OpenCV on windows. Pip is a de facto standard package-management system used to install and manage software packages written in Python and it usually comes in installed when you install Python. If you do not have Python installed, I would suggest download it from here. Use this command in the command prompt to install OpenCV:

```bash
pip install opencv-python
```

## For Mac

You can use homebrew to intall OpenCV as it makes it really easy and you just have to use this command for installing:

```bash
brew install opencv
```

You can also refer to the following resources to know further about **[OpenCV](https://opencv.org/)**
