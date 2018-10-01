A dataset and Jupyter notebook for exploring Lesson 1 of the Fast.ai Deep Learning 1 course using barbies vs. women, instead of the original Kaggle Dogs and Cats dataset.

@semih suggested classifying photos of barbies vs. women: http://forums.fast.ai/t/wiki-lesson-1/9398/

barbieswomen.zip contains training and validation data set up using the folder structure required for fast.ai. I created the dataset using two python scripts:

googleimagesdownload: https://github.com/hardikvasa/google-images-download

You can install this using `pip install google-images-download`

make_train_valid.py from https://github.com/prairie-guy/ai_utilities

`googleimagesdownload` requires a machine with a chrome browser and the appropriate chromedriver (see the googleimagesdownload GitHub repo for instructions). Otherwise, you are limited to 100 images.

Download the images using these commands. 

```
googleimagesdownload -k "woman" -o "barbieswomen" --format jpg --usage_rights labeled-for-reuse -l 150 --chromedriver ./chromedriver
googleimagesdownload -k "barbie" -o "barbieswomen" --format jpg --usage_rights labeled-for-reuse -l 150 --chromedriver ./chromedriver
```

Examine the images and remove incorrect images. I removed all paintings and images that were not clearly women or barbies. I also removed images that contained both women and barbies, since the model is forced to choose between one or the other classification.

After removing inappropriate images, run

```
make_train_valid.py barbieswomen --train .80 --valid .20
```

Now compress the directory and upload to your VM.
If using Paperspace through SSH, execute:

```
scp barbieswomen.zip paperspace@<your machine's public IP address>:./barbieswomen.zip
```