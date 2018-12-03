# Python install for Machine Learning Tensorflow Keras Ubuntu 18.04 (In development)
Python install for Machine Learning Tensorflow Keras Ubuntu 18.04 (CPU)

###### What you will need :

- Ubuntu 18.04
- Sudo rights

Hello! This post will aim at installing Python for Machine Learning with Keras on Ubuntu 18.04.
At the end of this tutorial you will have installed the following:
- Docker
- Tensorflow Docker image including keras

First, we need to install Docker.
Go to https://docs.docker.com/install/ and download the Docker CE (Community Edition) for Ubuntu. Direct link to Ubuntu install: https://docs.docker.com/install/linux/docker-ce/ubuntu/#os-requirements.

Install the program.

Open a terminal
Run
>docker run --runtime=nvidia -rm -it -p 8888:8888 tensorflow/tensorflow:latest

You will have some lines saying that you launched a Jupyter server and giving a token like this: .

Enter the following address in a web browser
>localhost:8888

You will be asked to enter your token.

Once it is done, you're good to go inside your Jupyter Notebook!


You can try to run the following "hello world"
```
import tensorflow as tf
mnist = tf.keras.datasets.mnist

(x_train, y_train),(x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

model = tf.keras.models.Sequential([
  tf.keras.layers.Flatten(),
  tf.keras.layers.Dense(512, activation=tf.nn.relu),
  tf.keras.layers.Dropout(0.2),
  tf.keras.layers.Dense(10, activation=tf.nn.softmax)
])
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

model.fit(x_train, y_train, epochs=5)
model.evaluate(x_test, y_test)
```

The result should be something like that showing the training:

![alt text](https://github.com/pleboulanger/Python-install-for-Machine-Learning-Tensorflow-Keras-Ubuntu-18.04/blob/master/MNIST.PNG)

###### Sources :
https://www.tensorflow.org/install/docker
