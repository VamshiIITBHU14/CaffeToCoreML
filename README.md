# CaffeToCoreML
Hey'll!
There are a lot of tutorials/ open source projects on how to use **Vision** and **CoreML** frameworks for **Object Detection** in real world using iOS apps using **.mlmodels** given by Apple. But seldom in reality, do we get a **.mlmodel** available suiting our use case. 

**CAFFE** is one of the
most famous Deep Learning frameworks used to train ML models (more details here: http://caffe.berkeleyvision.org)

Here, I took up a **Caffe model for the Oxford 102 flower dataset**, which was converted to **CoreML model** using **coremltools python package**.

`oxford102.caffemodel` can be downloaded at https://drive.google.com/uc?export=download&confirm=PXEh&id=0B0HbJVlOlJ3SVVNyMDQwR3FRYWc . Please not that along with `oxford102.caffemodel`, we will also need `flower-labels.txt` and `deploy.prototxt` files in order to successfully **convert .caffemodel to .mlmodel** 

Also note that this conversion from `.caffemodel to .mlmodel` is only possible with `**Python2.7**`



Once downloaded the above mentioned three files, here are the steps used for conversion:

1) Put all the three downloaded files in a folder, say FlowerClassifier.
2) Add a python file, say convert-script.py in the same folder.
3) Add the script below to your convert-script.py file.

```
import coremltools

caffe_model = ('oxford102.caffemodel', 'deploy.prototxt')
labels  = 'flower-labels.txt'

coreml_model = coremltools.converters.caffe.convert(
caffe_model,
class_labels = labels,
image_input_names = 'data'
)

coreml_model.save('FlowerClassifier.mlmodel')
```

4) Now, launch Terminal in your Mac, activate Python2.7 using command ```source python27/bin/activate```

5) Then cd into your folder (***FlowerClassifier***)
6) Then run the script using command ```python convert-script.py```.

Voila! 2-3 minutes later you will have your FlowerClassifier.ml model present in your FlowerClassifier folder. 

For those who want to skip the conversion part and directly use FlowerClassifier.mlmodel , you can download it here (https://drive.google.com/file/d/0B1ghKa_MYL6meDBHT2NaZGxkNzQ/view) . Please note that I have not uploaded this model in my project owing to size constraints. 

Just download the .mlmodel, drag and drop it into your project directory and test the ap on different flowers in real world.

***Final project looks like this:***

<img width="465" alt="screen shot 2017-12-13 at 5 40 17 pm" src="https://user-images.githubusercontent.com/21070922/33938271-dbc2c69a-e02c-11e7-95a7-f3c0e608e59a.png">





