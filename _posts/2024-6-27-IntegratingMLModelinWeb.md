---
layout: post
title: Integrating 🛠️ Tensorflow custom models in Frontend Applications💻.
subtitle: How does model interact with frontend?
excerpt_image: 
categories: MachineLearning
tags: [MachineLearning]
---

## Just for Motivation

"It’s about leveraging AI responsibly and strategically to enhance, not replace, the human elements of our roles." - Rajat Monga

Building an AI model is one part, for interacting with user we need an interface where the second  part comes up 'Integration' to a forntend application. In this blog will explain how to integrate an AI model to a frontend application (here I'm using Angular but same procedure will followed for everything).

### table of contents
1. Convertion of custom model
2. Evaluating the model
3. Integrating the model

# 1. Convertion of Model

Generally, tensorflow models can be saved in different file formats, to support in web we required to change them into supported formats. For that tensorflow is providing two options one is tfjs for the web in which tfjs is only supports models in .json format. Another one is Tensorflow/tfjs-tflite which supports model in .tflite format (tflite also supports in mobile development). Based upon our requirements we will convert the model to that particular format. Tflite is lite weighted models where the size of the model will be very low compared to other formats.

### let's see how to convert the custom models:

I prefer ipynb notebook you can also do it in .py too. For two methods you need to install tensorflowjs.

```python
!pip install tensorflowjs
```

- Converting model to json:

converting the model to json file using the following command
```python
!tensorflowjs_converter \
    --input_format keras \
    --output_format tfjs_layers_model \
    /content/model.h5 \
    /content/mouth_model
```
- Converting model to tflite:
converting the model to tflite file.
```python
import tensorflow as tf
model = tf.keras.models.load_model('/tmp/model.h5')
converter = tf.lite.TFLiteConverter.from_keras_model(model)
tflmodel = converter.convert()
file = open( '/tmp/model.tflite' , 'wb' )
file.write( tflmodel )
```
Refer to (https://www.tensorflow.org/lite/models/convert/convert_models) for more understanding.

# 2. Evaluating the model

Before integrating we need to know about the model functionality .In my understanding there are three things to keep in my mind what is accepatable input and it's shape, what is the expected output and main importantly any preprocessing is required or not.

Let us assume we have a model to classify cats and dogs images. To display this </br>
input,shape : 2D array,[168,244] - {What we need to send to the model}</br>
output : class_name - {what we get from the model}</br>
preprocessing : image should be converted into 2D array . {what we need to do before sending the input to the model}.

<div style="text-align:center;"> 
    <img src="https://tinyurl.com/vyjkzv6m" height="500px" width="500px">
</div>

After looking into the evaluation we know how to achieve the task (classify cats and dogs images).

# 3. Integrating the model

## using tfjs for json model
install Tensorflow.js 

```node
npm i @tensorflow/tfjs
```
TensorFlow.js is an open-source hardware-accelerated JavaScript library for training and deploying machine learning models.

1. import tensorflowjs 
```typescript
import * as tf from '@tensorflow/tfjs';
```

2. load the model
```typescript
async function loadModel() {
    const model = await tf.loadLayersModel('path/to/model.json');
    return model;
}
```

3. Preprocess the model
```typescript
function preprocessInput(image: HTMLImageElement) {
    const tensor = tf.browser.fromPixels(image)
        .resizeNearestNeighbor([168, 244]) // Change size here if necessary
        .toFloat()
        .expandDims();
    return tensor;
}
```

4. Make Predictions
```typescript
async function makePrediction(image: HTMLImageElement) {
    const model = await loadModel();
    const inputTensor = preprocessInput(image);
    const predictions = model.predict(inputTensor) as tf.Tensor;
    const results = predictions.dataSync();
    return results;
}
```

## using tfjs-tflite for tflite model

1. Firstly, install tensorflow/tfjs-tflite
```node
npm i @tensorflow/tfjs-tflite
```

2. Load the model
```typescript
async function loadTFLiteModel() {
    const model = await tf.loadTFLiteModel('path/to/model.tflite');
    return model;
}
```

3. Preprocess the model input
```typescript
function preprocessInputTFLite(image: HTMLImageElement) {
    const tensor = tf.browser.fromPixels(image)
        .resizeNearestNeighbor([168, 244]) // Change size here if necessary
        .toFloat()
        .expandDims();
    return tensor;
}
```

4. Make Predictions
```typescript
async function makePredictionTFLite(image: HTMLImageElement) {
    const model = await loadTFLiteModel();
    const inputTensor = preprocessInputTFLite(image);
    const predictions = model.predict(inputTensor) as tf.Tensor;
    const results = predictions.dataSync();
    return results;
}
```

Here We Gooo..! 
By following the above steps you are able to integrate the ML models in Angular and same steps can be implemented for other frontend frameworks also.

Thank you for reading.

