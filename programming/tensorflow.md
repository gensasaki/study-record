## TensorFlow

### Install
#### OS X or Linux
Run the following command to set up the environment:  
```
conda create -n tensorflow python=3.6  
source activate tensorflow  
conda install pandas matplotlib jupyter notebook scipy scikit-learn  
pip install tensorflow
```

### Hello, world!
```
import tensorflow as tf  

# create TensorFlow object called tensor  
hello_constant = tf.constant("Hello, world!")

with tf.Session() as sess:
    # Run the tf.constant operation in the session
    output = sess.run(hello_constant)
    print(output)
```
